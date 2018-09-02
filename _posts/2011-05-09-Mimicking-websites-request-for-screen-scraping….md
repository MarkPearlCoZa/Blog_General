---
layout: post
title: Mimicking websites request for screen scraping…
tags: 
category: General
---
Introduction
I don’t do web programming… I have been programming client applications for years and consider myself a WPF/Silverlight developer. The web thing always seemed a bit scary in its stateless environment with limited functionality and cross browser headaches. That was until recently when apparently HTML5 was going to kill Silverlight and I eventually decided that I would need to get educated and up to date.

Since that decision I have re-accustomed myself with HTML, CSS & JavaScript. Rediscovered why most of my web programming friends hate Internet Explorer 7 or pre, come to some sort of comfort that Silverlight is a very different technology to HTML5 and that there will be place for both of them and got the overwhelming urge to do screen scraping or find some really useful REST service that I can plug into. So today’s post is about the last, some found some data I have been dying to scrape from the web, but never knew enough of the basics to actually figure out how to get it…

The Website
So, let’s first look at the website I want to mimic and scrape and why it exists…

A few years ago we had a lot of drama in Southern Africa, mainly with Zimbabwe which was going through political crisis – the net result being people were flooding South Africa illegally from our neighbouring countries. Of course once these illegal immigrants settled here they did not or could not go home and needed some plan on how to legally get residence in the country. One or two resourceful con men came up with a plan on how to achieve this – they decided they would steal people’s identities, then marry these illegal immigrants to the identities until the illegals qualified for the relevant visa’s “legally”. A brilliant plan if I say so myself, and one that only had one problem with it. When the average South African citizen would one day decide they wanted to get married they would go an apply for it at Home Affairs, only to discover that they had already been married to someone for several years (unknown to them).

Obviously when this massive scam was discovered the Home Affairs department got the brunt of it and needed to be seen to be proactive about the whole thing and in an attempt to do this they put up a site where any South African citizen could enter their ID number and get their marital status displayed back.. (see link below).

http://www.home-affairs.gov.za/enquiry/marital/status/marital_status.asp

While I cannot think of any real useful application of a site like this other than to verify when you are married, I got a bee in my bonnet and wanted to make use of this service. Now I say service because that is all I was interested in. I wanted to be able to send an ID number via a service and get the marital status. I did not want to have to send my users through to the site, I wanted to do it all in the background. My problem was this… as far as I know there was no publicly available service that does this… you have the site or nothing…

My Plan
I recently watched a series from Harvard on screen scraping. Basically the idea is when a site does not provide the information you need via a feed or publically available service, then as a last resort you can go and “scrape” their site for the information you need. It’s a bit messy, but it works…

So,after watching this series the idea came to me, I could do the same with the website. I would need to somehow mimic a person going to the site and entering their ID number and then scrape the result and package it in a result and wrap it in a service of my own.

To achieve this I would have two challenges….

I would need to figure out how to simulate entering in an ID number
I would need to scrape the result
Today I am going to talk about my attempts at point one. If anyone is interested in point 2 I might cover it in a future post…

Mimicking the submission process
Well, in my limited knowledge of how things work on the web there are really two main ways people send data in a classic website, they either call a Get or Post request. When looking at the site I wanted to scrape I could see from the URL that no additional parameters were being passed other than the location of the result page… this meant my life was going to be a little harder than I initially thought. Instead of simply calling a URL with the ID as a parameter I would need to do this in a post request.

2011-05-09 07-17-09 AM

 

So I knew I needed to mimic the post request but I had no idea on what it looked like. I have for a few years heard of a tool called Fiddler which I was told basically allowed you to see everything going across the wire… I figured today was the day I would give it a try…

Firing up fiddler for the first time I opened my browser and again made a submission. As I submitted the site fiddler showed a bunch of requests going through…

fiddler12011-05-09 07-21-27 AM

I figured this was what I needed to mimic. Checking out the inspector pane on fiddler I got to see a bit more data… including what the header looked like as well as the body of the post.

fiddler22011-05-09 07-24-11 AM

 

My First Attempt
After looking at the results from fiddler my reasoning was as follows… if I could make a post that mimicked the header exactly, then the server would have no way of telling me whether I was itself requesting the information or a third party and it would just spit out the data I needed. I was working on the assumption that it didn’t have any session tokens or anything like that…. which I figured was a safe bet since there were no login passwords or anything.

A bit of googling and what do you know, I found someone who has put up a post on exactly what I wanted to do…

http://www.dijksterhuis.org/simple-class-to-submit-post-a-web-form-from-csharp/

So copying his code I changed the URL I had the following…

 

using System;
using System.Net;
using System.Web;
using System.Collections;
using System.IO;

namespace WebRequestExample
{

    public class WebPostRequest
    {
        WebRequest theRequest;
        HttpWebResponse theResponse;
        ArrayList theQueryData;

        public WebPostRequest(string url)
        {
            theRequest = WebRequest.Create(url);
            theRequest.Method = "POST";
            theQueryData = new ArrayList();
        }

        public void Add(string key, string value)
        {
            theQueryData.Add(String.Format("{0}={1}", key, HttpUtility.UrlEncode(value)));
        }

        public string GetResponse()
        {
            // Set the encoding type
            theRequest.ContentType = "application/x-www-form-urlencoded";

            // Build a string containing all the parameters
            string Parameters = String.Join("&", (String[])theQueryData.ToArray(typeof(string)));
            theRequest.ContentLength = Parameters.Length;

            // We write the parameters into the request
            StreamWriter sw = new StreamWriter(theRequest.GetRequestStream());
            sw.Write(Parameters);
            sw.Close();

            // Execute the query
            theResponse = (HttpWebResponse)theRequest.GetResponse();
            StreamReader sr = new StreamReader(theResponse.GetResponseStream());
            return sr.ReadToEnd();
        }

    }

    public class MainClass
    {
        public static void Main(string[] args)
        {
            WebPostRequest myPost = new WebPostRequest("http://www.home-affairs.gov.za/enquiry/marital/status/get_maritalstatus.asp");
            //myPost.Add("keyword", "void");            
            Console.WriteLine(myPost.GetResponse());
            Console.ReadLine();
        }
    }
}
Running it in fiddler it gave me the following results

Attempt11

 

attemp1

So it seemed to work, but the header was totally different from the original post and it was missing some information and of course I just made the call, I had not included any information like ID number…

Modifying my main call, I added the IDNumber parameter into the body of the call…

 

 public static void Main(string[] args)
        {
            WebPostRequest myPost = new WebPostRequest("http://www.home-affairs.gov.za/enquiry/marital/status/get_maritalstatus.asp");
            myPost.Add("idno", "8001015009087");            
            Console.WriteLine(myPost.GetResponse());
            Console.ReadLine();
        }
 

 

Now when I run the application it absolutely dies. Looking at it through fiddler I see it returns a 417 error.

Attempt12

 

Second Attempt
Looking at my first attempt I could see that when I did not pass through an ID number, I got no issues, but as soon as I started to include the ID Number the server was saying to me that my message was not in the correct format (417).

In my second attempt I looked at changing the header to get it to be identical to the one from the site.

Looking at Fiddler I could see that the successful call had cookies with the call as well as different parameters, so modifying the header was what I wanted to do.

using System;
using System.Net;
using System.Web;
using System.Collections;
using System.IO;
using System.Net.Cache;

namespace WebRequestExample
{    

    class WebPostRequest
    {
        private const string WEB_URL = "http://www.home-affairs.gov.za";
        private const string WEB_URL_REQUEST_PAGE = "http://www.home-affairs.gov.za/enquiry/marital/status/marital_status.asp";
        private Uri WebUri = new Uri(WEB_URL);
        WebRequest theRequest;
        HttpWebResponse theResponse;
        ArrayList theQueryData;

        public WebPostRequest(string url)
        {
            
            theRequest = HttpWebRequest.Create(url);
            HttpWebRequest theReq = (HttpWebRequest) theRequest;

            theReq.CookieContainer = new CookieContainer();            
            theReq.CookieContainer.Add(WebUri, new Cookie("ASPSESSIONIDQABATARR", "LCNLJGOBEJKMHMMMPDFGGHFG", "/"));
            theReq.CookieContainer.Add(WebUri, new Cookie("ASPSESSIONIDSCBDSBQR", "EHKNDMKCOHHLOBPKEDBEPHKH", "/"));
            theReq.AutomaticDecompression = DecompressionMethods.GZip | DecompressionMethods.Deflate;
            theReq.Headers.Add(HttpRequestHeader.Pragma, "no-cache");
            theReq.Headers.Add(HttpRequestHeader.AcceptLanguage, "en-ZA");                        
            
            theReq.Accept = "text/html, application/xhtml+xml, */*";
            theReq.UserAgent = "Mozilla/5.0 (compatible; MSIE 9.0; Windows NT 6.1; WOW64; Trident/5.0)";
            theReq.ContentType = "application/x-www-form-urlencoded";
            theReq.Referer = WEB_URL_REQUEST_PAGE;
                        
            theRequest.Method = "POST";            
            theQueryData = new ArrayList();
        }

        public void Add(string key, string value)
        {            
            theQueryData.Add(String.Format("{0}={1}", key, HttpUtility.UrlEncode(value)));
        }

        public string GetResponse()
        {
            // Set the encoding type
            theRequest.ContentType = "application/x-www-form-urlencoded";           

            // Build a string containing all the parameters
            string Parameters = String.Join("&", (String[])theQueryData.ToArray(typeof(string)));
            theRequest.ContentLength = Parameters.Length;
            theRequest.UseDefaultCredentials = false;            

            // We write the parameters into the request
            StreamWriter sw = new StreamWriter(theRequest.GetRequestStream());
            sw.Write(Parameters);
            sw.Close();            

            // Execute the query               
            theResponse = (HttpWebResponse)theRequest.GetResponse();
            StreamReader sr = new StreamReader(theResponse.GetResponseStream());
            return sr.ReadToEnd();
        }

    }

    class MainClass
    {
        public static void Main(string[] args)
        {                       
            WebPostRequest myPost = new WebPostRequest("http://www.home-affairs.gov.za/enquiry/marital/status/get_maritalstatus.asp");            
            myPost.Add("idno", "8001015009087");                             
            Console.WriteLine(myPost.GetResponse());
            Console.ReadLine();
        }
    }
}
 

Attempt2
This almost got me there, everything was identical to the site call except I could not get rid of the Expect: 100-continue part of the header…

When I ran the program again, I still got the irritating 417 error.

 

Final Attempt
After more searching on the web I eventually found out how to get rid of the Expect: 100-continue in the header. A slight modification to the WebPostRequest method and I ended up with this…

using System; 
using System.Net; 
using System.Web; 
using System.Collections; 
using System.IO; 
using System.Net.Cache;

namespace WebRequestExample 
{   

    class WebPostRequest 
    { 
        private const string WEB_URL = "http://www.home-affairs.gov.za"; 
        private const string WEB_URL_REQUEST_PAGE = "http://www.home-affairs.gov.za/enquiry/marital/status/marital_status.asp"; 
        private Uri WebUri = new Uri(WEB_URL); 
        WebRequest theRequest; 
        HttpWebResponse theResponse; 
        ArrayList theQueryData;

        public WebPostRequest(string url) 
        { 
            System.Net.ServicePointManager.Expect100Continue = false; 
            theRequest = HttpWebRequest.Create(url); 
            HttpWebRequest theReq = (HttpWebRequest) theRequest;

            theReq.CookieContainer = new CookieContainer();            
            theReq.CookieContainer.Add(WebUri, new Cookie("ASPSESSIONIDQABATARR", "LCNLJGOBEJKMHMMMPDFGGHFG", "/")); 
            theReq.CookieContainer.Add(WebUri, new Cookie("ASPSESSIONIDSCBDSBQR", "EHKNDMKCOHHLOBPKEDBEPHKH", "/")); 
            theReq.AutomaticDecompression = DecompressionMethods.GZip | DecompressionMethods.Deflate; 
            theReq.Headers.Add(HttpRequestHeader.Pragma, "no-cache"); 
            theReq.Headers.Add(HttpRequestHeader.AcceptLanguage, "en-ZA");                        
            
            theReq.Accept = "text/html, application/xhtml+xml, */*"; 
            theReq.UserAgent = "Mozilla/5.0 (compatible; MSIE 9.0; Windows NT 6.1; WOW64; Trident/5.0)"; 
            theReq.ContentType = "application/x-www-form-urlencoded"; 
            theReq.Referer = WEB_URL_REQUEST_PAGE; 
                        
            theRequest.Method = "POST";            
            theQueryData = new ArrayList(); 
        }

        public void Add(string key, string value) 
        {            
            theQueryData.Add(String.Format("{0}={1}", key, HttpUtility.UrlEncode(value))); 
        }

        public string GetResponse() 
        { 
            // Set the encoding type 
            theRequest.ContentType = "application/x-www-form-urlencoded";          

            // Build a string containing all the parameters 
            string Parameters = String.Join("&", (String[])theQueryData.ToArray(typeof(string))); 
            theRequest.ContentLength = Parameters.Length; 
            theRequest.UseDefaultCredentials = false;           

            // We write the parameters into the request 
            StreamWriter sw = new StreamWriter(theRequest.GetRequestStream()); 
            sw.Write(Parameters); 
            sw.Close();           

            // Execute the query               
            theResponse = (HttpWebResponse)theRequest.GetResponse(); 
            StreamReader sr = new StreamReader(theResponse.GetResponseStream()); 
            return sr.ReadToEnd(); 
        }

    }

    class MainClass 
    { 
        public static void Main(string[] args) 
        {                       
            WebPostRequest myPost = new WebPostRequest("http://www.home-affairs.gov.za/enquiry/marital/status/get_maritalstatus.asp");            
            myPost.Add("idno", "8001015009087");                             
            Console.WriteLine(myPost.GetResponse()); 
            Console.ReadLine(); 
        } 
    } 
} 

This worked!!! If I looked at the header in fiddler it matched the one from the original site perfectly and now I was getting out some information out.

So now all I have to do is scrape the result and extract the info I wanted and there you go…

The Conclusion
As you can probably tell I am by no means an expect on web facing applications, but this was a fun exercise to do to learn if it is possible to simulate a site. After getting this far the thought came t me about how the same principle could be applied to doing a brute force attempt at breaching a login page etc.

Anyhow, the net result, best practices with generating session tokens on pages where you want to protect your information etc would just make someone's life a little harder… Hope someone find this info useful!
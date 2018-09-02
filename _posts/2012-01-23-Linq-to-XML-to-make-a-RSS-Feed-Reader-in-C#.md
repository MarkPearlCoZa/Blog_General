---
layout: post
title: Linq to XML to make a RSS Feed Reader in C#
tags: 
category: Tech
---
Today I thought I would just list a little tutorial on how to make an RSS feed reader in C#. The code is very simple…

    public class RssFeedReader
    {
        public IEnumerable<Post> ReadFeed(string url)
        {
            var rssFeed = XDocument.Load(url);

            var posts = from item in rssFeed.Descendants("item")
            select new Post
            {
                Title = item.Element("title").Value,
                Description = item.Element("description").Value,
                PublishedDate = item.Element("pubDate").Value
            };

            return posts;
        }
    }

    public class Post
    {
        public string PublishedDate;
        public string Description;
        public string Title;
    }
An example of using this would be as follows…

    class Program
    {
        static void Main(string[] args)
        {
            var posts = new RssFeedReader().ReadFeed(@"http://www.pwop.com/feed.aspx?show=dotnetrocks&filetype=master");
            Console.WriteLine(posts.ToList().Count);
            Console.ReadLine();
        }
    }
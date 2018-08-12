---
layout: post
title: AutoMapper
tags: 
category: General
---

No more left-right code
 

I was listening to a legacy Polymorphic Podcast and heard about a really great time saver called AutoMapper.

AutoMapper uses a convention-based matching algorithm to match up source to destination values. It is extremely useful when you have a lot of “left-right code” and want to automate the passing of the values.

For instance, assume you had two objects (e.g. of type stClient & Client), and you wanted to mass copy the values from the stClient object to the Client object.

~~~
public struct stClient
{
    public string Name;
    public int Age;
}
 
public class Client
{
    public string Name { get; set; }
    public int Age { get; set; }        

    public void Load(long ID)
    {
        tblClient table = new tblClient();
        stClient data = table.Get(ID);
        Name = data.Name;
        Age = data.Age;            
    }
}
~~~
 
One way you could achieve this is to manually pass the value’s across. However, if you had quite a few values, this would become a laborious task.

With AutoMapper you can bypass this totally. To use AutoMapper you would first have to create a mapping between the types of objects.

~~~
Mapper.CreateMap(typeof(stClient), typeof(Client));
~~~

You then simply call the mapping method.

~~~
public void Load(long ID)
{
    tblClient table = new tblClient();
    stClient data = table.Get(ID);
    Mapper.Map(data, this);
}
~~~
 
And there you go… AutoMapper matches the values from the one object to the other and copies the values across.

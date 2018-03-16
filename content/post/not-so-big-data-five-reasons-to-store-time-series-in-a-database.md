+++
Categories = ["R","rstats","postgreSQL","SQL"]
date = "2018-02-28T11:11:05+01:00"
title = "Not so big data: 5 reasons to store time series in a database (anyway)"
Tags = ["rstats","time series","SQL","not so big data"]
Description = "Integrity, collaboration, web technologies, access management and cross platform interoperability are just 5 of many good reasons to store time series in a real database."
+++

My data are not that big, should I store it in a database? I get this question from various flavors of researchers, data analysts and even from their new school version, data scientists. And almost every single time my advice is: yes, use a database, preferrably a SQL database. Here are five reasons why... <!--more-->

Admittedly, size does matter when it comes to data. But my claim for using a SQL database when it comes to storing your (scientific) time series data for the long run doesn't even need the big data buzzword to back it up. So here's why:

1. Consistent, permanent storage
Many scientific users like to use interactive environments like the Python or R ecosystems to analyze data. As long as it is not too much for their RAM, people love to handle data in memory. It's fast and convenient. But what if your session crashes? What if you need to switch off your computer? 
People write data to disk in propietary binary formats or spreadsheet formats that may or may not be text. But who checks your Excel file for duplicate identifiers? From the outside looking in, how do I know what's the difference between time_series1.xlsx and time_series1.csv? And where do I even find those files? Was it /nas/storage/project_y/draft_x/ramyczekiwicz.xlsx?

A database fixes all of that. Thanks to unique constraints on primary keys, you cannot not add an existing series twice. There are standard, select, insert, update and delete processes which have been used billions of times and therefore are fast and stable -- very much unlike a custom made double check. Also, it's immediately clear which is the most recent version. And ... 


2. You're not alone! 
We hardly work on projects alone. There's at least a supervisor or a reviewer and maybe even a collaborator. And even if you really work as a one-man-army who owns lone ranger collectibles, there might be a customer or at least a consumer of your data. 

Whenever you have to share data, a database is a good option. Who enjoys e-mail ping pong with double-digit MB attachments? Is it even secure? Who else sees the data? Instead of storing data locally on some hard disk, a remote database helps to find reliable answers to all of these questions. And for starters, you don't need a big time GUI. A standard ODBC connection, a set of prepared queries helps Excel aficionados to work with a database just like it were a set of very flexible and consistent files. 

3. All your favorite web technologies can access a DB
Speaking of sharing, you may want to publish data.
How about providing it through a (REST) web interface? 
To me, this is the most important advantage of a database over a file system for the advanced user who wants to spread information. 
Basically any language you might want to use to implement a web interface for your users can speak to a SQL database. Java, check. Python, check. PHP, check. Microsoft languages, check. And the list goes on and on. Plus there's ODBC in case your favorite language is not familiar with the SQL dialect your database uses. With the help of frameworks like the [Django REST Framekwork](http://www.django-rest-framework.org/), [Spring](https://spring.io/) or the lightweight [Slim microframework](https://www.slimframework.com/), to name only few it is easy to set up a server which makes your data available through simple URL endpoints. And the [KONG microservice](https://getkong.org/) is super useful to secure, manage and extend your interfaces and other microservices.


4. Control who accesses what 
Dish out database access to single users on table or schema basis. With state-of-the-art databases like PostgreSQL 9.6+, you can even do so on a (record) / time series basis . Use Row Level Security (RLS) to single out a specific series and allow a particular user group to access those. Now try to do that in a textfile. Databases do not only improve one's security concept, but also help to track changes who made changes to production level information. 


5. Cross-platform interoperability
Who (at least in academia) has not worked together with Windows, OSX and Linux contributors in the same project? Even if you haven't read one of the most [famous blog posts in computer science](https://www.joelonsoftware.com/2003/10/08/the-absolute-minimum-every-software-developer-absolutely-positively-must-know-about-unicode-and-character-sets-no-excuses/), the word *encoding* might ring a *fr¡™¢k!ng¡!•ªøö!* bell. You know, the French and the Germans with their accents and umlauts and let alone the Chinese with their everything. But even in national project with everybody speaking the same language, there be the Microsoft lovers and haters, the latter splitting into Linux hackers and OSX people. When you use a SQL database all of these systems and tastes will just read the data and live on happily ever after. No more *'Hey my Excel can't read what your open something just wrote, it must by a mac problem'*. 


And yes, there are working license cost free solutions. I will soon present an updated version of *timeseriesdb*, an R and PostgreSQL based solution which was specifically designed for use with time series in official statistics.









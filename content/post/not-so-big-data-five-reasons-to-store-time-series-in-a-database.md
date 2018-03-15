+++
Categories = ["R","rstats","postgreSQL","SQL"]
date = "2018-02-28T11:11:05+01:00"
title = "Not so big data: 5 reasons to store time series in a database (anyway)"
Tags = ["rstats","time series","SQL","not so big data"]
Description = "Integrity, collaboration, web technologies, access management and cross platform interoperability are just 5 of many good reasons to store time series in a real database."
+++

My data are not that big, should I store it in a database? I get this question in various flavors from statisticians, data analysts and even from their new school version, data scientists. And almost every single time my advice is: yes, use a database, preferrably a SQL database. Here are five reasons why... <!--more-->

Admittedly, size does matter when it comes to data. But my claim for using a SQL database when it comes to storing your (scientific) time series data for the long run doesn't even need the big data buzzword to back it up. So here's why:

1. Consistent, permanent storage
Many scientific users like to use interactive environments like the Python or R ecosystems to analyze data. As long as it is not too much for your RAM, people love to handle in memory. It's fast and convenient. But what if your session crashes? What if you need to switch off your computer? 
People write data to disk in propietary binary formats, spreadsheet format that may or may not be text. But who checks your Excel file for duplicate identifiers of our time series? (Sure you could write a function - but honestly who does that?) How do I know what's the difference between time_series1.xlsx and time_series1.csv? Is it just the file format or the content?

A database. fixes all of that. Thanks to contraints such unique constraints on primary keys, you cannot not add an existing series twice. There are standard, insert, update and delete processes which have been used billions of times and therefore are fast and stable -- very much unlike a custom made double check. Also, it's immediately clear which is the most recent version.  


2. You're not alone 
We hardly work on projects alone. There's at least a supervisor or reviewer and maybe even a collaborator. And even if you really work as a one-man-army and who owns lone ranger collectibles, there might be a customer or at a least a consumer of your data. 

Whenever you have to share data, a database is a good option. Who enjoys e-mail ping pong with double-digit MB attachments? Is it even secure? Who else sees the data? Instead of storing data locally on some hard disk, a remote database helps to find reliable answer to all of these questions. 

3. All your favorite web technologies can access a DB
Speaking of sharing, you may want to publish data. How about providing it through a REST interface?
Basically any language you might want to use to implement a web interface for your users can speak to a SQL database. Java, check. Python, check. PHP, check. And the list goes on and on. And a did not even mention standards like ODBC. With the help of frameworks like the Django REST Framekwork, Spring or Slim 


4. Control who accesses what 
Dish out database access to single users on table, schema or general basis. 
With state-of-the-art databases like PostgreSQL 9.6+, you can even do so on time series basis. Use Row Level Security (RLS) to single out a specific series and allow a particular user group to access those. Now try to do that in a textfile. Databases do not only improve one's security concept, but also help to track changes who made changes to production level information. 


5. Cross-platform interoperability
Who (at least in academia) has not worked together with Windows, OSX and Linux contributors in the same project. 





And yes, there are working license cost free solutions. I will present an updated R and PostgreSQL based solution for time series in official statistics here soon. 









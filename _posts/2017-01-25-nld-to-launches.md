---
title:  "nld.to Launches"
date:   2017-01-25 23:00:00 -0600
categories: show256
author: mjcarroll
---
For New Leaf Digital, we thought that it would be helpful to have our own short URL, where we could provide easy links to members, sponsors, and presenters.  Once I saw that [bit.ly](http://bit.ly) Enterprise cost [$995 per month](https://www.quora.com/How-much-do-vanity-URL-shorteners-cost) for vanity URLS, I thought that I could find a better solution.

I found (YOURLS)[https://github.com/YOURLS/Y OURLS], which is a PHP/MySQL-based URL shortener.  I already had an (Amazon Lightsail)[https://amazonlightsail.com] Ubuntu box that was idle ($5 per month), so I set it up on there.

The only major thing that I ran into was that there were errors creating a few of the tables with MariaDB on 16.04.  I worked through the issue by following this (Github Issue)[https://github.com/YOURLS/YOURLS/issues/2125], in particular the following command got the tables to create properly.:

```
MariaDB [yourlsdb]> CREATE TABLE IF NOT EXISTS yourls_url (keyword varchar(200) BINARY NOT NULL,url text BINARY NOT NULL,title text CHARACTER SET utf8,timestamp TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,ip VARCHAR(41) NOT NULL,clicks INT(10) UNSIGNED NOT NULL, PRIMARY KEY (keyword), KEY timestamp (timestamp), KEY ip (ip))
-> ENGINE=MyISAM;
```

---
id: 344
title: How to Move MySQL Databases.
date: 2011-09-25T07:03:09+00:00
author: Rolando Islas
layout: post
guid: http://ontheweb.tk/tutorials/how-to-move-mysql-databases/
permalink: /how-to-move-mysql-databases/
dsq_thread_id:
  - 2447038101
categories:
  - Random
---
There is that time when you decide to change webhost and you need to move your databases. You may even just doing a backup. This tutorial will simplify how to do it easily.

**Exporting your database:**

  1. You need to go into your &#8220;phpmyadmin&#8221;. Accessing this may be different depending on where you are hosting. It can usually be accessed through zpanel or similar.
  2. Select your database. In my phpmyadmin it was on the left. 
  3. Click on the Export tab from the top.
  4. By default everything should be selected. Make sure it is set to sql. Select save as file and you can leave the compression as none, but I recommend putting seting it to compressed.
  5. Click go and your database should start downloading.

**Importing your database:**

  1. In your phpmyadmin create a new database. Leave it empty.
  2. Select your database and click the import tab at the top.
  3. Browse for your file. (e.g. sql, zip)
  4. Click on the go button. After your file uploads and executes your database should be restored.
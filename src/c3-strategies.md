# Strategies

There are 3 kinds of different websites in artistreit. Generally, there are 4 ways to improve the websites in Artisreit.

- Simple php websites
- Wordpress website
- Landing pages

### How to improve them.

1. Cache

    - Simple Cache

        The simple cache is cache the data used to render the PHP file. For example, When a user requests a PHP file that needs to access the database, the cache can quickly provide the data for the PHP. Because getting cache data takes less time than querying a database, the Cache can improve the response time and increase the concurrent online user.

    - Nginx Cache

        Nginx is hight performace web service and is good at serveing static files.
        As the [Cacheable PHP Enviroment](./c2_1-cacheable_php_enviroment.md) said, the nginx cache is a fast cgi cache, the final response of the request can be cached in disk as static files

        Nginx cache can improve most comparing other solutions for the current websites in Artis Reit. The most important fact is this solution can be used in all websites in Azure and doesn't care about if the website is WordPress or a simple PHP website. There are more than 10 times speed improvements after applying the Nginx cache.

        One thing to note is that, when changing the apache php enviroments to nginx enviroment, many apache config need to be convert to nginx config, such rewite rules, redirect rules, and so on.

    - Browser Cache

        Browser Cache is the cache in the user browser. By setting the http header properties, the resource can be used after the first request.

        Browser cache needs to do on a specific page of the PHP according to the scene.


2. Refactor

    refactor doesn't change the appearance and the functions of the website, but improves the code structure and environment.

    - For simple websites, we can refactor the website to pure HTML website without any PHP files and migrate them to `azure static web app`, or we just reduce PHP and do some other optimisation.

    - For wordpress websites, we can do little to improve them. 

    - For landing pages, it's better to convert them to htmls, css and js, then deploy them to CDN.

3. Remake

    Completely redesign and develop some website using better technology and solutions

    we use jamstack architecture, so they remake need to using a static tool like nextjs and react components.



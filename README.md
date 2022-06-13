# SEO_Sitemaps
A lightweight module which provides request handlers for sitemap.xml and robots.txt. Furthermore, it provides helper functions and a template implementation for setting up multiple sitemaps for an efficient sitemap strategy.

## Get Started
###Prerequisites:
- download the ‘Runtime Core Wrapper` module into your project.

### Setup:
When you open the module in the project navigation in Studio Pro you will find the _UseMe folder.

This folder contains the steps that need to be taken to set up the module.

- Copy or move the reference implementation in the `_UseMe/1. Setup/A. Copy Implementation` folder to a new module and include (right click, ->include in project) the copied or moved documents in the project.
- GetSiteMapXML, example microflow that returns sample sitemap.xml contents.
- GetRobotsTXT, example that returns sample robots.txt contents.
- SiteMapService, a published rest service template that specifies endpoints for multiple sitemaps.
- Add the `StartSEO` Java Action to the startup microflow of the project.
- Configure the robots txt microflow, e.g. `GetRobotsTXT`
- Configure the sitemap xml microflow, e.g. `GetSiteMapXML`

### Canonical Domain
To make sure you’re not having content indexed for different domains where the content is actually the same you can configure the `CanonicalDomain` constant.

The `GetCanonicalDomain` microflow references a java action which is not included in the module. This java action in available in the ‘Runtime Core Wrapper’ module.

### Enable Multiple Sitemaps
To enable multiple sitemaps you need to utilize the Published REST Service `SiteMapService` which has to be copied to a newly created module. 

In the StartSEO java action in the startup microflow you need to configure the microflow: `GetSiteIndexXML`.
This microflow will return a site index representing the endpoints available in the published sitemap rest service.

### Creating a microflow returning a sitemap
- Create a new XML export mapping document
- Select XML Schema
- Find the `Sitemap_0_9` schema and select it.
- Configure the XML as mentioned in the documentation and map it to the entity that contains the url in an attribute.
- Create a new microflow.
- The microflow should retrieve a list of objects of which an attribute has the value of a url.
- Add an export mapping activity and select the xml export mapping you created.
- Return the value as an string and use the return variable in the end activity of the microflow. 
- Configure the newly created microflow in the startup java action or connect the microflow to an endpoint in the published rest service.

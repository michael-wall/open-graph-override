This is a POC to show how the Open Graph meta tags can be overridden in Liferay DXP.

This POC replaces the default og:title value with the following syntax: 

<meta property="og:title" content="MW - Home - Liferay DXP - mw custom title... 1718359263543">

This POC was built with Java 11 for Liferay DXP 7.4 U92.

The OpenGraphTopHeadDynamicInclude.java class generates the og:title and other og meta tags, the steps to create a customization for DXP 7.4 are as follows:

1. Create a custom OSGi fragment module to export the following internal classes from Liferay module com.liferay.layout.seo.web.fragment: 
- com.liferay.layout.seo.web.internal.configuration
- com.liferay.layout.seo.web.internal.util
2. Create a custom OSGi module using the correct Liferay source code version of OpenGraphTopHeadDynamicInclude.java from the com.liferay.layout.seo.web module and make the required changes in this class. The og:title is set with this line:
printWriter.println(_getOpenGraphTag("og:title", title));

Deployment steps:
1. Build and deploy the custom modules.
2. Blacklist the following component in System Settings > Module Container > Component Blacklist (through the GUI or with a config file): com.liferay.layout.seo.web.internal.servlet.taglib.OpenGraphTopHeadDynamicInclude

This is a POC to show how the Open Graph meta tags can be overridden in Liferay.

This POC was built with Java 11 for Liferay DXP 7.4 U92.

Deployment steps:

1. Build and deploy the custom modules.
2. Blacklist the following component in System Settings > Module Container > Component Blacklist (through the GUI or with a config file): com.liferay.layout.seo.web.internal.servlet.taglib.OpenGraphTopHeadDynamicInclude

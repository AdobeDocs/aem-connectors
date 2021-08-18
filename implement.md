Implementing an AEM Connector
=============================

Provided below are useful references for building [AEM Connectors](https://www.adobe.io/apis/experiencecloud/aem/aemconnectors.html) and should be read in conjunction with guidance on [submitting](submit.md) and [maintaining](maintain.md) connectors.

Note that a Developer license for AEM can be obtained through the [Adobe Exchange Program](https://partners.adobe.com/exchangeprogram/experiencecloud).

Common Integration Patterns
---------------------------

AEM is a cutting-edge web experience management solution and offers many potential areas of integrations. Common integration patterns include:

*   Pulling data from an external system into AEM. For example, exporting contact information from a CRM to make it available to a wider audience visiting an AEM-powered website.  Implementations should use Sling's [Scheduled Jobs](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#scheduled-jobs), which guarantees that the job is executed even if containers go down. Code should be designed to assume that the job can potentially be triggered more than once. 
*   Exporting data from AEM into an external system. For example, newsletter subscription settings submitted on an AEM-powered website to a CRM.
*   Retrieving assets from AEM. For example, an external Content Management System (CMS) referencing an asset stored in AEM Assets. Or as another example,  a PIM system linking to an image in AEM Assets.
*   Storing assets in AEM. For example, a Marketing Resource Management (MRM) system storing an approved asset in AEM Assets.
*   Configuring and rendering a custom UI component. For example, allow an author to drag and drop a video component and configure a specific video to play on the live site. Learn more about [AEM components](https://experienceleague.adobe.com/docs/experience-manager-65/developing/components/components-basics.html).
*   Acting on an asset with a partner service. For example, sending an asset to a video platform when a page is published.
*   Analyzing a site, page, or asset in the AEM admin console. For example, making SEO recommendations for an existing or unpublished page.
*   Page-level access to user data maintained by an external service. For example, leverage demographic information to personalize the site experience. Read about [ContextHub](https://experienceleague.adobe.com/docs/experience-manager-65/developing/personlization/contexthub.html), a framework for storing, manipulating, and presenting context data. 
*   Translating site copy or asset metadata. See the [AEM Translation Framework Bootstrap Connector](https://github.com/Adobe-Marketing-Cloud/aem-translation-framework-bootstrap-connector) for sample code using the AEM Translation Framework, which is the preferred implementation of translation connectors.
*   Connecting with an eCommerce engine. Learn about the [AEM Content and Commerce](https://experienceleague.adobe.com/docs/experience-manager-65/commerce/introduction.html).

Useful Documentation
--------------------

AEM's [documentation](https://experienceleague.adobe.com/docs/experience-manager-65.html) provides valuable insights into developing in AEM. Below are some specific technical topics and references that you may find useful while implementing an AEM connector:

*   [How to Develop AEM Projects Using Eclipse](https://experienceleague.adobe.com/docs/experience-manager-65/developing/devtools/howto-projects-eclipse.html)
*   [Best Practices](https://experienceleague.adobe.com/docs/experience-manager-65/developing/bestpractices/best-practices.html) for various AEM topics
*   Adobe Consulting Services (ACS) [AEM Samples](http://adobe-consulting-services.github.io/acs-aem-samples/) for well-commented code to help educate AEM developers
*   Configuring a [Cloud Service Configuration](https://experienceleague.adobe.com/docs/experience-manager-65/developing/extending-aem/extending-cloud-services/extending-cloud-config.html) dialog to make it easy for customers to setup the connector

*   The various documentation links in the Common Integration Patterns section of this article

Community Resources 
--------------------

In addition to the static documentation above, Adobe and the AEM community offer resources to help bring a connector to market:

*   The Adobe Community's [AEM Forum](http://help-forums.adobe.com/content/adobeforums/en/experience-manager-forum/adobe-experience-manager.html) is an active site where your peers ask and respond to questions
*   Additional Adobe technical resources are available to certain partner levels. Learn more about the [Adobe Exchange Program](https://partners.adobe.com/exchangeprogram/experiencecloud).
*   If your organization would like implementation help, consider Adobe's [Professional Services](http://www.adobe.com/marketing-cloud/service-support/professional-consulting-training.html) team or see the [Solution Partner Finder](https://solutionpartners.adobe.com/home/partnerFinder.html) for a list of Adobe's partners across the globe

Technical Requirements
----------------------

Below is a list of best practices for AEM Connectors. While we highly recommend that all AEM connectors listed in the Adobe Marketing Cloud Exchange adhere to these requirements, they will be explicitly enforced for those connectors whose binaries are distributed via AEM Package Share. Connectors distributed via AEM Package Share are vetted by an Adobe Approver, giving customers greater confidence that the solution functions correctly. Learn more about [submitting a connector](submit.md).

*   Build with a supported JDK and test the connector in a supported environment, which can be referenced [here](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/introduction/technical-requirements.html).
*   Due to security concerns, do not reference [the deprecated](http://sling.apache.org/documentation/the-sling-engine/service-authentication.html#deprecation-of-administrative-authentication) SlingRepository.loginAdministrative() and ResourceResolverFactory.getAdministrativeResourceResolver() methods.
*   Uninstalling a connector should not break AEM functionality.
*   Upgrading a connector should seamlessly replace the prior version. See the [connector maintenance article](maintain.md) to understand the common customer upgrade process. 
*   Upgrading AEM should not break the connector. Of course, it is only possible to test this for connectors targeting older versions of AEM.   
*   Works with main supported browsers, in particular IE11, Firefox, and Chrome.
*   Works on both Windows and Linux. Pay special attention to path case sensitivity, which differs on the two OSes.

Design Considerations
---------------------

When writing a connector, consider the following decisions:

*   Which versions of AEM should be supported? Partners may benefit from surveying their customers to determine what AEM versions to build for and maintain. Read more about requirements and best practices for [maintaining a connector](maintain.md) and providing a seamless upgrade path for customers upgrading to newer versions of AEM.
*   Support localization for connectors that will be used in different regions. Learn about [localizing components](https://experienceleague.adobe.com/docs/experience-manager-65/developing/components/internationalization/i18n.html).
*   Check if the AEM instance uses a proxy before requesting remote URLs, retrieving the HttpClient using org.apache.http.osgi.services.HttpClientBuilderFactory.newBuilder().build();

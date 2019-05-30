Submitting an AEM Connector
===========================

Provided below is useful information for submitting [AEM Connectors](https://www.adobe.io/apis/experiencecloud/aem/aemconnectors.html) and should be read in conjunction with articles about [implementing](implement.md) and  [maintaining](maintain.md) connectors.

AEM Connectors are listed on the [Adobe Exchange](https://marketing.adobe.com/resources/content/resources/en/exchange/marketplace.html), where they can be discovered by customers. We recommend distributing the package binary through AEM's Package Share, which implies some vetting of the package by an Adobe Exchange partner team representative.

The steps below outline the process for submitting a connector, after it has been [implemented](implement.md):

1.  Create a package: AEM connectors typically include an AEM package that is built and often installed using AEM Package Manager. Learn about using AEM Package Manager to [create a package](https://docs.adobe.com/docs/en/aem/6-3/administer/content/package-manager.html#Creating a New Package), including filling out the fields under [package settings](https://docs.adobe.com/docs/en/aem/6-3/administer/content/package-manager.html#Package Settings).


2.  Optionally, upload the package to AEM Package Share: As described above, hosting the package through AEM's Package Share site is recommended. Learn about [accessing Package Share](https://docs.adobe.com/docs/en/aem/6-3/administer/content/package-manager.html#Package Share) and [uploading a package](https://docs.adobe.com/docs/en/aem/6-3/administer/content/package-manager.html#Uploading a package). 


3.  If uploaded to Package Share, an Adobe Admin will review the connector to ensure it functions correctly with activities that include:
4.  installing the package
    *   executing integration tests to validate proper execution, such as looking for regressions in core AEM code, broken UI, and reductions in overall performance.
    *   validating that it does not introduce unwarranted warnings or errors into the logs.
    *   ensuring that it does not interfere with upgrading the version of an AEM instance.
    *   validating that certain design patterns are followed; for example, translation connectors should use the [AEM Translation Framework.](https://docs.adobe.com/docs/en/aem/6-3/administer/sites/translation/tc-tic.html)
5.  Register for the [Adobe Exchange Program](https://partners.adobe.com/exchangeprogram/experiencecloud), which serves as the hub for vendors to manage their relationship with Adobe and their connectors.


6.  Create a listing for the connector in Adobe Exchange by clicking the appropriate button on the Adobe Exchange Program's [main page](https://partners.adobe.com/exchangeprogram/experiencecloud). Fill out all required fields in the multi-page form and submit. Consider referencing documentation and videos to inform customers how the connector works. 

    See this [App Listing Guide](https://partners.adobe.com/exchangeprogram/experiencecloud/build/ec-exchange.html) for best practices in filling out the form.

    If the package was uploaded to package share, make sure to indicate so by choosing "Experience Manager Package Share" for the "installation instructions" question. This will ensure that an Adobe administrator is aware of the connection between the listing and the binary submission in package share.


7.  Once the listing is approved, the connector will be listed on Adobe Exchange and the package will be made available on Package Share, if uploaded there. The listing description will reference how the consumer can gain access to the connector, either in Package Share or a partner's own web infrastructure.

Also read the [maintenance article](maintain.md) to understand a partner's commitments, once the initial connector has been approved and listed.

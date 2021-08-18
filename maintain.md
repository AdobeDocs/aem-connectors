Maintaining an AEM Connector
============================

This article contains information about maintaining an [AEM Connector](https://www.adobe.io/apis/experiencecloud/aem/aemconnectors.html) and should be read in conjunction with articles about [implementing](implement.md) and [submitting](submit.md) connectors.

Even after the initial submission, there may be reasons for a partner to update its AEM Connector, either due to a new release of AEM or independent of that – for example, to add features or to fix bugs. This article outlines the process for both scenarios and also describes a customer's typical process for validating connectors when upgrading AEM. 

Connector Updates due to AEM Releases
-------------------------------------

AEM releases software via several [release vehicles](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/update-release-vehicle-definitions.html) and partners should pay particular attention to full releases and service packs to ensure that their connectors continue to function. If code changes are necessary, connectors should be updated so customers enjoy a seamless upgrade process. Since customers are in full control of when they upgrade, partners may choose to support multiple versions of their connector, based on their knowledge of which versions of AEM are most popular with their customers. 

### Full releases

A full release is a major AEM version upgrade once a year, historically in the April time frame. The current version is 6.3. 

Partners are expected to test their connector with each major version to ensure that it continues to function. If a new version of a connector is needed, the resubmission process will depend on whether the package binary is distributed through AEM Package Share.

If hosted in Package Share 

*   A partner can choose to replace the existing Package Share listing or create a new one. It's preferable to replace an existing listing, which implies backwards compatibility with  previous AEM versions, but here are some reasons for why this might not be possible:
    *   the new AEM version has an API signature change
    *   the new AEM version has an incompatible OSGI dependency
    *   there are substantial code changes, either in AEM or the partner service (e.g. a new cloud API), making it difficult to support multiple versions of code in the same package
*   Indicate to the Adobe Exchange partner team whether the existing Package Share listing should be used by marking the same Name and Group ID in package metadata. This ensures that the package is uploaded to the same JCR location under /etc/packages so AEM Package Manager shows an option to update the package.
*   The package's description field should reference the supported AEM versions.
*   The AEM Tested With and AEM Built With fields should reflect the highest version supported for the package. 
*   Email the Adobe Exchange partner team ([aemc-support@adobe.com](mailto:aemc-support@adobe.com)) when the updated package has been uploaded. When the Adobe Exchange partner team approves the listing, the associated Adobe Exchange listing will be updated with a reference to the latest package share link.

If not hosted in Package Share

*   Email the Adobe Exchange partner team with the desired changes in the listing description, which should reference the newly supported AEM versions. 

### Service packs

A service pack is an update to a specific full release and potentially released every quarter.  Service Packs include important bug fixes and potentially product enhancements.

Partners are expected to test their connector with each service pack to ensure that it continues to function. While it's less likely that a service pack will introduce major changes, if a new version of a connector is necessary, follow the same resubmission process as outlined under the "Full releases" section. 

### Other release types

While rare, a hot fix or cumulative fix pack can theoretically modify connector functionality. If a customer who has applied a patch notifies the partner that the connector has stopped functioning correctly, follow the same resubmission process as outlined under the "Full releases" section.

Connector updates independent of AEM releases
---------------------------------------------

A partner may decide to modify a connector for various reasons, including introducing new features or fixing bugs. The resubmission process is similar to what is outlined in the "Full releases" section under AEM Releases above, although the partner should also include more context about the changes in the new description. 

Customer AEM upgrade process and connector validation
-----------------------------------------------------

Typically, a customer upgrading AEM will follow the process outlined below, validating that partner connectors continue to work. If a connector has issues, the customer will likely reach out to the partner.

1.  Customers use AEM X.1 with connector Y.1
2.  Adobe announces AEM X.2
3.  Customers install X.2 on a test environment to see how it fits their business and see if the connector works
4.  If the connector doesn’t work, they'll open a ticket directly with the partner
5.  The partner updates their package and posts it as Y.2 and we certify the build on AEM X.2
6.  Partner reaches out to the customer and lets them know that Y.2 build is available.
7.  Customer installs the Y.2 build on top of Y.1 connector.  It is assumed that the packages are created in such a way that the Name and Group ID are consistent for the connector to be upgraded without having to uninstall an older version.
8.  Customer tests the environment and upon success adds both AEM X.2 and connector Y.2 to their release plan.

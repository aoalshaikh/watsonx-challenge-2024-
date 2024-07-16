# IBM OpenPages
## About OpenPages

IBM OpenPages® is an AI-driven, highly scalable governance, risk, and compliance (GRC) solution. OpenPages enables organizations to centralize siloed risk management functions within a single environment to identify, manage, monitor, and report on risk and regulatory compliance. 

### Reporting Fragments
A reporting fragment is typically either a chart, crosstab or list that can be placed on a page of the application so that the user can see a visual representation of data alongside the page data.

#### Using Images in Reporting Fragments
 You can insert an image in a report that is used in Reporting Fragments.
The images that you insert must first be uploaded to both the IBM® Cognos® Analytics server and the IBM OpenPages® server. Images must be gif or jpg format.

After you upload the image, you must use a relative path to refer to the image. The relative path should be valid on both the IBM Cognos Analytics server and the IBM OpenPages server.
Follow these best practices:
- Copy the image to the following folders:
  - `<COGNOS_HOME>\webcontent\bi\images`
  - `<OP_HOME>/wlp-usr/shared/apps/op-apps.ear/sosa.war/images`
- Access the image in the report that is used for the reporting fragment by using the relative path ../images/<image file name>.

#### Framework Models
OpenPages® includes a set of framework models. The following table lists the models and their namespaces.

|  Model |  Description | Namespaces |
|---|---|---|
| Assurance and Testing | For audit and assurance management use cases | AUD1, AUD2, DEFAULT |
| Model Risk and Data Privacy | For model risk and data privacy use cases | DEFAULT, DPM1, MRG1, MRG2  |
| Operational Risk and Control | For operational risk and financial control management use cases | DEFAULT, ORM1, ORM2, ORM3, RA1, RA2, SOX1 |
| Policy and Compliance | For regulatory and policy management use cases | DEFAULT, MAND1, MAND2, POL1, RCM1, RCM2, RCM3, REGAPP1 |
| Resilience and Continuity | For IT governance, business continuity, third party management, and operational resilience use cases | BCM1, BCM2, BCM3, BCM4, BCM5, BCM6, BCM7, BCM8, BCM9, DEFAULT, ITG1, ITG2, TPRM1 |
| Platform Reporting | The Level 0 framework model, which is used to run platform reports | DEFAULT |
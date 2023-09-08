![](https://img.shields.io/badge/STATUS-NOT%20CURRENTLY%20MAINTAINED-red.svg?longCache=true&style=flat)

# Important Notice
This public repository is read-only and no longer maintained. For the latest sample code repositories, visit the [SAP Samples](https://github.com/SAP-samples) organization.

[![REUSE status](https://api.reuse.software/badge/github.com/SAP-samples/localization-toolkit-s4hana-cloud-tax-id-validation)](https://api.reuse.software/info/github.com/SAP-samples/localization-toolkit-s4hana-cloud-tax-id-validation)

## Localization Toolkit for SAP S/4HANA Cloud: Validating a Tax ID Format

This repository contains the sample code for the [Validate a Tax ID format](https://blogs.sap.com/2019/08/16/validate-a-tax-number/) tutorial.

*This code is only one part of the tutorial, so please follow the tutorial before attempting to use this code.*

### Description

Information provided captures the implementation details required to validate Tax ID format, and how to do such an extension on the SAP S/4HANA Cloud. This extensibility is a part of [Localization Toolkit for SAP S/4HANA Cloud](https://community.sap.com/topics/localization-toolkit-s4hana-cloud).

### Prerequisites
You have administrative access to SAP S/4HANA Cloud and have implementation experience on the system. Coding experience is also necessary, since this extensibility solution requires implementation of a coding logic.

### Authorizations

Business Role	| Business Role ID
---------------|------------------
Configuration Expert – Business Network Integration	| SAP _ BR _ CONF _ EXPERT _ BUS _ NET _ INT
Master Data Specialist – Business Partner Data |	MASTER _ SPECIALIST

### Implementation
For example, you want to validate the format of the Tax Identification Number (TIN) for a country and display an error message in case of an invalid format. You can do so by implementing a cloud BAdI to validate the Tax ID format.  You will also have to create a repository to store custom error messages.

Implement the validation logic by creating a new enhancement implementation, using the Custom Logic option in the Custom Fields and Logic App. Write the implementation logic for Tax ID format validation in the Draft Logic area and publish the new enhancement implementation.

* Note: Enter a solution specific to the purpose of this implementation in the code logic. This is necessary because the BAdI does not have an option to set a filter.
You need to implement/adapt (duplicate) the provided sample code for each country, for which, the check is applicable.
Additionally, you need to replace the XX country code placeholders in the coding with country code used in your implementation.

Since the BADI implementation is referring to the tables where the custom messages are stored, the system will display error messages when you implement the BADI, and before you have created the required message class(es).
You can create a custom message while implementing the validation logic, or use an existing custom message. If you create a new custom message, you must publish the validation logic only after storing this message in the repository.

## Known Issues
There are currently no known issues.

## How to obtain support
If you have issues with this sample, please visit the SAP community page or contact your SAP contact to obtain support. In case you observe any defect in the product usage itself, kindly use the SAP Product support channel and raise an incident adequately for the defects observed. You can also post questions directly to our [community](https://answers.sap.com/questions/ask.html?primaryTagId=9af4d745-1754-4882-b057-f8f904c0a5f8).

## License
Copyright (c) 2020 SAP SE or an SAP affiliate company. All rights reserved.
This project is licensed under the Apache Software License, version 2.0 except as noted otherwise in the [LICENSE](LICENSE) file.

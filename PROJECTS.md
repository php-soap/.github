# Next big projects

This page contains a list of the next big projects!

1. [Better types](#better-types)
2. Encoding / Decoding


## Better types

Currently we rely on PHP's ext-soap to provide us all type information. This information is far from complete.
It lacks information like minOccurs, maxOccurs, enum values, namespaces, ...
Therefore, it is currently not possible to generate better types.

In order to fix this issue, we need to fetch all information from the WSDL instead of from the information PHP provides.

This project will consist out of following tasks:


WSDL 1 parsing:

* Create a system that can parse the WSDL 1 operations, messages and types into usable objects
* This system needs to be extendable into parsing WSDL 1 services and bindings
* This system needs to be extendable into parsing WSDL 2 interfaces
* This system needs to be usable for encoding / decoding SOAP requests
* Intensive XSD parsing
* Testing on various big / frequently used WSDLs


Metadata:

* Convert the parsed information into the metadata structure of php-soap/engine so that it can be used for code generation.
* Revision the metdata format based on the newly acquired information.


Code generation:

* [Make sure that code generation can deal with the new minOccurs / maxOccurs information](https://github.com/phpro/soap-client/blob/master/docs/known-issues/ext-soap.md#occurs)
* [Investigate if XSD enums can be mapped into PHP enums or provide a middle-way.](https://github.com/phpro/soap-client/blob/master/docs/known-issues/ext-soap.md#enumerations)
* [Provide a better way to generate duplicate types based on namespace information.](https://github.com/phpro/soap-client/blob/master/docs/known-issues/ext-soap.md#duplicate-typenames)


With the changes above, we aim to get rid of all commonly reported issues on phpro/soap-client.
This will lead to better generated code for your soap-client which makes it easier to use in combination with static analyzers. In short: you will have less bugs in production! From our side, we will have less maintenance overhead once everything runs in a stable way.

https://github.com/phpro/soap-client/blob/master/docs/known-issues/ext-soap.md#duplicate-typenames





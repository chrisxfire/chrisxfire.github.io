---
title: "notes > swe > protocols > wsdl"
date: 2022-06-21T14:10:55-0600
draft: true
---
# WSDL – Web Service Description Language
Describes the functionality of a SOAP-based web service.

# WSDL elements
`<types>`The XML schema data types used by the web service.
`<message>`The data elements for each operation.
`<portType>`Defines a web service, its operations, and messages involved.
`<binding>`The protocol and data format for each port type.

# WSDL skeleton example
`<definitions>`

`<types>`
`data type definitions........`
`</types>`

`<message>`
`definition of the data being communicated....`
`</message>`

`<portType>`
`set of operations......`
`</portType>`

`<binding>`
`protocol and data format specification....`
`</binding>`

`</definitions>`

# Partial WSDL example
<messagename="getTermRequest">
<partname="term"type="xs:string"/>
</message>

<messagename="getTermResponse">
<partname="value"type="xs:string"/>
</message>

<portTypename="glossaryTerms">
<operationname="getTerm">
<inputmessage="getTermRequest"/>
<outputmessage="getTermResponse"/>
</operation>
</portType>

*From <<https://www.w3schools.com/xml/xml_wsdl.asp>>*

Types of portType
One-wayThe operation can receive a message but will not return a response
Request-responseThe operation can receive a request and will return a response
Solicit-responseThe operation can send a request and will wait for a response
NotificationThe operation can send a message but will not wait for a response

# WSDL Binding to SOAP
WSDL bindings define the message format and protocol details for the web service:
<messagename="getTermRequest">
<partname="term"type="xs:string"/>
</message>

<messagename="getTermResponse">
<partname="value"type="xs:string"/>
</message>

<portTypename="glossaryTerms">
<operationname="getTerm">
<inputmessage="getTermRequest"/>
<outputmessage="getTermResponse"/>
</operation>
</portType>

<bindingtype="glossaryTerms"name="b1">
<soap:bindingstyle="document"
 transport="http://schemas.xmlsoap.org/soap/http"/>
<operation>
<soap:operationsoapAction="http://example.com/getTerm"/>
<input><soap:bodyuse="literal"/></input>
<output><soap:bodyuse="literal"/></output>
</operation>
</binding>

*From <<https://www.w3schools.com/xml/xml_wsdl.asp>>*

## binding element attributes
namethe service's name
typethe service's port (like `glossaryTerms`)

## soap:binding element attributes
style"rpc" or "document"
transportlike <http://schemas.xmlsoap.org/soap/http>

# Web Services Description Language (WSDL)
- XML-based interface description language
- Services in WSDL are a collection of endpoints called *ports*
- Port—network address + reusable binding
- Messages—abstract descriptions of data being exchanged
- Port types—abstract collections of supported operations
- Reusable binding—concrete protocol + data format specification
- Operations and messages are bound to concrete network protocol and message format


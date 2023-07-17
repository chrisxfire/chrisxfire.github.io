---
title: notes > software engineering > protocols > wsdl
date: 2022-06-21T14:10:55-0600
draft: false
weight: 1
---
# WSDL – Web Service Description Language
Describes the functionality of a SOAP-based web service.

# WSDL elements
- `<types>` - The XML schema data types used by the web service.
- `<message>` - The data elements for each operation.
- `<portType>` - Defines a web service, its operations, and messages involved.
- `<binding>` - The protocol and data format for each port type.

# WSDL skeleton example
```xml
<definitions>

    <types>
        data type definitions........
    </types>

    <message>
        definition of the data being communicated....
    </message>

    <portType>
        set of operations......
    </portType>

    <binding>
        protocol and data format specification....
    </binding>

</definitions>
```

# Partial WSDL example
```xml
<messagename="getTermRequest">
<partname="term"type="xs:string"/>
</message>

<messagename="getTermResponse">
<partname="value"type="xs:string"/>
</message>

<portType name="glossaryTerms">
    <operation name="getTerm">
    <inputmessage="getTermRequest"/>
    <outputmessage="getTermResponse"/>
    </operation>
</portType>
```

From <https://www.w3schools.com/xml/xml_wsdl.asp>

# Types of portType
- One-way - The operation can receive a message but will not return a response
- Request - responseThe operation can receive a request and will return a response
- Solicit - responseThe operation can send a request and will wait for a response
- Notification - The operation can send a message but will not wait for a response

# WSDL Binding to SOAP
WSDL bindings define the message format and protocol details for the web service:
```xml
<message name="getTermRequest">
    <part name="term"type="xs:string"/>
</message>

<message name="getTermResponse">
    <part name="value"type="xs:string"/>
</message>

<portType name="glossaryTerms">
    <operation name="getTerm">
        <inputmessage="getTermRequest"/>
        <outputmessage="getTermResponse"/>
    </operation>
</portType>

<binding type="glossaryTerms" name="b1">
<soap:bindingstyle="document"
 transport="http://schemas.xmlsoap.org/soap/http"/>
<operation>
    <soap:operationsoap Action="http://example.com/getTerm"/>
    <input><soap:body use="literal"/></input>
    <output><soap:body use="literal"/></output>
</operation>
</binding>
```

From <https://www.w3schools.com/xml/xml_wsdl.asp>

## binding element attributes
- `name` - the service's name
- `type` - the service's port (like glossaryTerms)

## soap:binding element attributes
- `style` - "rpc" or "document"
- `transport` - like <http://schemas.xmlsoap.org/soap/http>

# Web Services Description Language (WSDL)
- XML-based interface description language
- Services in WSDL are a collection of endpoints called *ports*
- Port—network address + reusable binding
- Messages—abstract descriptions of data being exchanged
- Port types—abstract collections of supported operations
- Reusable binding—concrete protocol + data format specification
- Operations and messages are bound to concrete network protocol and message format


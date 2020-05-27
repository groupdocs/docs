---
id: convert-specific-pages
url: conversion/java/convert-specific-pages
title: Convert specific pages
weight: 3
description: "This article demonstrates how to convert specific document pages by page number using GroupDocs.Conversion for Java API."
keywords: Convert page, Convert pages, Convert specific pages
productName: GroupDocs.Conversion for Java
hideChildren: False
---
[**GroupDocs.Conversion**](https://products.groupdocs.com/conversion/java) also provides the feature to convert selected page number. 

Here are the steps to follow: 

*   Create new instance of [Converter](https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion/Converter) class and pass source document path as a constructor parameter
*   Instantiate the proper [ConvertOptions](https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion.options.convert/ConvertOptions)class e.g. ([PdfConvertOptions](https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion.options.convert/PdfConvertOptions)**, **[WordProcessingConvertOptions](https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion.options.convert/WordProcessingConvertOptions)**, **[SpreadsheetConvertOptions](https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion.options.convert/SpreadsheetConvertOptions)etc.)
*   Set [setPages](https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion.options.convert/ConvertOptions#setPages(java.util.List))property of the [ConvertOptions](https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion.options.convert/ConvertOptions)instance with list of desired page number to be converted
*   Call [convert](https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion/Converter#convert(java.lang.String,%20com.groupdocs.conversion.options.convert.ConvertOptions)) method of [Converter](https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion/Converter)class instance and pass filename for the converted document and the instance of [ConvertOptions](https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion.options.convert/ConvertOptions) from the previous steps

  
Following code snippet shows how to convert first and third pages from the source document:

```csharp
Converter converter = new Converter("sample.docx");
PdfConvertOptions options = new PdfConvertOptions();
options.setPages(Arrays.asList( 1, 3));
converter.convert("converted.pdf", options);
```

## More resources

### GitHub Examples

You may easily run the code above and see the feature in action in our GitHub examples:

*   [GroupDocs.Conversion for .NET examples, plugins, and showcase](https://github.com/groupdocs-conversion/GroupDocs.Conversion-for-.NET)
    
*   [GroupDocs.Conversion for Java examples, plugins, and showcase](https://github.com/groupdocs-conversion/GroupDocs.Conversion-for-Java)
    
*   [Document Conversion for .NET MVC UI Example](https://github.com/groupdocs-conversion/GroupDocs.Conversion-for-.NET-MVC) 
    
*   [Document Conversion for .NET App WebForms UI Modern Example](https://github.com/groupdocs-conversion/GroupDocs.Conversion-for-.NET-WebForms)
    
*   [Document Conversion for Java App Dropwizard UI Modern Example](https://github.com/groupdocs-conversion/GroupDocs.Conversion-for-Java-Dropwizard)
    
*   [Document Conversion for Java Spring UI Example](https://github.com/groupdocs-conversion/GroupDocs.Conversion-for-Java-Spring)
    

### Free Online Document Converter Apps

Along with full-featured Java library we provide free Apps and free services for document conversion.

In order to see a full potential of GroupDocs.Conversion, you are welcome to convert DOC to PDF, DOC to XLSX, PDF to DOC, PDF to XLSX, PPT to DOC and more with **[Free Online Document Converter App](https://products.groupdocs.app/conversion)** or get a full advantage of **[Free Online Document Converter Suite](https://conholdate.app/features/document-converter-online)** with advanced conversion settings and many more enterprise built-in features.

**Please note** that more [premium features](https://conholdate.app/features), advanced options and enhanced document management experience is available for signed-in users at [conholdate.app](https://conholdate.app/) for **FREE**.  
If you don't own an account yet, register it now for free! No credit card is required!

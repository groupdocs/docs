---
id: convert-to-pdf
url: conversion/java/convert-to-pdf
title: Convert to PDF
weight: 3
description: "This article demonstrates how to convert any document to PDF format with couple Java code lines and GroupDocs.Conversion for Java."
keywords: Convert to PDF, Convert to PDF/A
productName: GroupDocs.Conversion for Java
hideChildren: False
---
Conversion to PDF format could be triggered by following below steps:

*   Create new instance of [Converter](https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion/Converter) class and pass source document path as a constructor parameter
*   Instantiate [PdfConvertOptions](https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion.options.convert/PdfConvertOptions)class.
*   Call [convert](https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion/Converter#convert(java.lang.String,%20com.groupdocs.conversion.options.convert.ConvertOptions)) method of [Converter](https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion/Converter) class instance and pass filename for the converted document and the instance of [PdfConvertOptions](https://apireference.groupdocs.com/java/conversion/com.groupdocs.conversion.options.convert/PdfConvertOptions) from the previous step.

The following code show how to convert any document to PDF. 

```csharp
Converter converter = new Converter("sample.docx");
PdfConvertOptions options = new PdfConvertOptions();
converter.convert("converted.pdf", options);
```

## More resources

### Advanced Usage Topics

To learn more about document viewing features, please refer to the [advanced usage section]({{< ref "conversion-java/developer-guide/advanced-usage/_index.md" >}}).

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

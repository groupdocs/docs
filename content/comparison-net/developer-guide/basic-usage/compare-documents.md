---
id: compare-documents
url: comparison-net/compare-documents
title: Compare documents
weight: 3
description: This article demonstrates how to compare Word, Excel, PowerPoint, Outlook, OneNote, PDF, Image, HTML, AutoCAD, Visio, OpenDocument, OneNote documents using GroupDocs.Comparison for .NET.
keywords: Compare documents, document comparison in C#
bookCollapseSection: true
productName: GroupDocs.Comparison for .NET
hideChildren: False
---

# Compare documents


# Documents comparison features

**[GroupDocs.Comparison](https://products.groupdocs.com/comparison/net)** allows to compare documents and save resultant document that shows changes between source and target document(s). Full list of supported document formats can be found [here](https://docs.groupdocs.com/display/comparisonnet/Supported+Document+Formats).  
Changes detection algorithms used by GroupDocs.Comparison allows to detect changes in different document parts and blocks:

*   Text blocks - paragraphs, words and characters;
*   Tables;
*   Images;
*   Shapes etc.

For better visual separation of detected changes added, modified or deleted document parts are highlighted with different colors:

*   Added document segments are highlighted with **blue**color;
*   Modified document segments are highlighted with **green** color;
*   Style changed document segments are highlighted with **green** color;
*   Deleted document segments are highlighted with **red**color.  
    

Changes styling coloring scheme can be customized if needed, changed text blocks can be marked with different formatting - italic, bold, underlined, strikethrough etc.  

Here are simple steps to compare two documents:

*   Instantiate [Comparer](https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer) object with source document path or stream;
*   Call [Add](https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/methods/add/index) method and specify target document path or stream;
*   Call [Compare](https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/methods/compare/index) method.

The following code snippet demonstrates the simplest case of documents comparison using couple lines of code. 

## Compare documents from local file

```csharp
using (Comparer comparer = new Comparer(“source.docx”))
{
	comparer.Add(“target.docx”);
	comparer.Compare(“result.docx”);
}
```

## Compare documents from stream

```csharp
using (Comparer comparer = new Comparer(File.OpenRead(“source.docx”)))
{
	comparer.Add(File.OpenRead(“target.docx”));
	comparer.Compare(File.Create(“result.docx”));
}
```

## More resources

### Advanced Usage Topics

To learn more about document comparison features, please refer to the [advanced usage section](Advanced%2Busage.html).

### GitHub Examples

You may easily run the code above and see the feature in action in our GitHub examples:

*   [GroupDocs.Comparison for .NET examples, plugins, and showcase](https://github.com/groupdocs-comparison/GroupDocs.Comparison-for-.NET)
    
*   [GroupDocs.Comparison for Java examples, plugins, and showcase](https://github.com/groupdocs-comparison/GroupDocs.Comparison-for-Java)
    
*   [Document Comparison for .NET MVC UI Example](https://github.com/groupdocs-comparison/GroupDocs.Comparison-for-.NET-MVC) 
    
*   [Document Comparison for .NET App WebForms UI Modern Example](https://github.com/groupdocs-comparison/GroupDocs.Comparison-for-.NET-WebForms)
    
*   [Document Comparison for Java App Dropwizard UI Modern Example](https://github.com/groupdocs-comparison/GroupDocs.Comparison-for-Java-Dropwizard)
    
*   [Document Comparison for Java Spring UI Example](https://github.com/groupdocs-comparison/GroupDocs.Comparison-for-Java-Spring)
    

### Free Online App

Along with full-featured .NET library we provide simple, but powerful free Apps.

You are welcome to compare your DOC or DOCX, XLS or XLSX, PPT or PPTX, PDF, EML, EMLX, MSGand other documents with free to use online **[GroupDocs Comparison App](https://products.groupdocs.app/comparison)**.

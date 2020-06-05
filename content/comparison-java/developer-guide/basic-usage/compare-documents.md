---
id: compare-documents
url: comparison/java/compare-documents
title: Compare documents
weight: 3
description: ""
keywords: 
productName: GroupDocs.Comparison for Java
hideChildren: False
---
# File comparison features

Changes detection algorithms used by** [GroupDocs.Comparison](https://products.groupdocs.com/comparison/java)** allows to detect changes in different document parts and blocks:

*   Text blocks - paragraphs, words and characters;
    
*   Tables;
    
*   Images;
    
*   Shapes etc.
    

For better visual separation of detected changes added, modified or deleted document parts are highlighted with different colors:

*   Added – **blue** 
    
*   Modified – **green**
    
*   Style – **green**
    
*   Deleted – **red**
    

Changes styling coloring scheme can be customized if needed, changed text blocks can be marked with different formatting - italic, bold, underlined, strikethrough etc.

 Here are simple steps to compare two documents: 

*   Instantiate [Comparer](https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison/Comparer)objectwith source document path or stream;
    
*   Call [add](https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison/Comparer#add(java.lang.String))method and specify target document path or stream.
    
*   Call [compare](https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison/Comparer#compare(java.lang.String))method.
    

The following code snippet demonstrates the simplest case of documents comparison using couple lines of code. 

## Compare documents from local file 

```csharp
Comparer comparer = new Comparer("C:\\source.pdf");
try {
    comparer.add("C:\\target.pdf");
    comparer.compare("C:\\result.pdf");
} finally {
    comparer.dispose();
}
```

## Compare documents from stream 

```csharp
Comparer comparer = new Comparer(new FileInputStream("C:\\source.pdf"));
try {
    comparer.add(new FileInputStream("C:\\target.pdf"));
    comparer.compare(new FileOutputStream("C:\\result.pdf"));
} finally {
    comparer.dispose();
}
```

## More resources

### Advanced Usage Topics

To learn more about document comparison features, please refer to the [advanced usage section]({{< ref "comparison-java/developer-guide/advanced-usage/_index.md" >}}).

### GitHub Examples

You may easily run the code above and see the feature in action in our GitHub examples:

*   [GroupDocs.Comparison for Java examples, plugins, and showcase](https://github.com/groupdocs-comparison/GroupDocs.Comparison-for-Java)
    
*   [GroupDocs.Comparison for .NET examples, plugins, and showcase](https://github.com/groupdocs-comparison/GroupDocs.Comparison-for-.NET)
*   [Document Comparison for Java App Dropwizard UI Modern Example](https://github.com/groupdocs-comparison/GroupDocs.Comparison-for-Java-Dropwizard)
    
*   [Document Comparison for Java Spring UI Example](https://github.com/groupdocs-comparison/GroupDocs.Comparison-for-Java-Spring)
    
*   [Document Comparison for .NET MVC UI Example](https://github.com/groupdocs-comparison/GroupDocs.Comparison-for-.NET-MVC)
    
*   [Document Comparison for .NET App WebForms UI Modern Example](https://github.com/groupdocs-comparison/GroupDocs.Comparison-for-.NET-WebForms)
    

### Free Online App

Along with full-featured Java library we provide simple, but powerful free Apps.

You are welcome to compare your DOC or DOCX, XLS or XLSX, PPT or PPTX, PDF, EML, EMLX, MSGand other documents with free to use online **[GroupDocs Comparison App](https://products.groupdocs.app/comparison)**.

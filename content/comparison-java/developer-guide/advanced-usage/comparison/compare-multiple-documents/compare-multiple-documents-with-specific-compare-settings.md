---
id: compare-multiple-documents-with-specific-compare-settings
url: comparison/java/compare-multiple-documents-with-specific-compare-settings
title: Compare multiple documents with specific compare settings
weight: 2
description: ""
keywords: 
productName: GroupDocs.Comparison for Java
hideChildren: False
---
**[GroupDocs.Comparison](https://products.groupdocs.com/comparison/java)** allows to compare more that 2 documents and specify some specific comparison options like styling for detected changes, comparison details level etc.

The following are the steps to compare multiple documents with specific options.

*   Instantiate [Comparer](https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison/Comparer)objectwith source document path or stream;
*   Call [add](https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison/Comparer#add(java.lang.String))method and specify target document path or stream. Repeat this step for every target document.
*   Instantiate [CompareOptions](https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison.options/CompareOptions)object and specify desired options;
*   Call [compare](https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison/Comparer#compare(java.lang.String,%20com.groupdocs.comparison.options.CompareOptions))method and pass [CompareOptions](https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison.options/CompareOptions)object from previous step.

The following code sample shows how to compare multiple documents with specific options.

## Compare multiple documents with specific compare settings from local disk

```csharp
Comparer comparer = new Comparer("C:\\source.pdf");
try {
    comparer.add("C:\\target1.pdf");
    comparer.add("C:\\target2.pdf");
    comparer.add("C:\\target3.pdf");

    final StyleSettings styleSettings = new StyleSettings();
    styleSettings.setFontColor(Color.YELLOW);

    CompareOptions compareOptions = new CompareOptions();
    compareOptions.setInsertedItemStyle(styleSettings);

    comparer.compare("C:\\result.pdf", compareOptions);
} finally {
    comparer.dispose();
}
```

## Compare multiple documents with specific compare settings from stream

```csharp
Comparer comparer = new Comparer(new FileInputStream("C:\\source.pdf"));
try {
    comparer.add(new FileInputStream("C:\\target1.pdf"));
    comparer.add(new FileInputStream("C:\\target2.pdf"));
    comparer.add(new FileInputStream("C:\\target3.pdf"));

    final StyleSettings styleSettings = new StyleSettings();
    styleSettings.setFontColor(Color.YELLOW);

    CompareOptions compareOptions = new CompareOptions();
    compareOptions.setInsertedItemStyle(styleSettings);

    comparer.compare(new FileOutputStream("C:\\result.pdf"), compareOptions);
} finally {
    comparer.dispose();
}
```

## More resources

### GitHub Examples

You may easily run the code above and see the feature in action in our GitHub examples:

*   [GroupDocs.Comparison for Java examples, plugins, and showcase](https://github.com/groupdocs-comparison/GroupDocs.Comparison-for-Java)
    
*   [GroupDocs.Comparison for .NET examples, plugins, and showcase](https://github.com/groupdocs-comparison/GroupDocs.Comparison-for-.NET)
    
*   [Document Comparison for Java App Dropwizard UI Modern Example](https://github.com/groupdocs-comparison/GroupDocs.Comparison-for-Java-Dropwizard)
    
*   [Document Comparison for Java Spring UI Example](https://github.com/groupdocs-comparison/GroupDocs.Comparison-for-Java-Spring)
*   [Document Comparison for .NET MVC UI Example](https://github.com/groupdocs-comparison/GroupDocs.Comparison-for-.NET-MVC) 
    
*   [Document Comparison for .NET App WebForms UI Modern Example](https://github.com/groupdocs-comparison/GroupDocs.Comparison-for-.NET-WebForms) 
    

### Free Online App

Along with full-featured Java library we provide simple, but powerful free Apps.You are welcome to compare your DOC or DOCX, XLS or XLSX, PPT or PPTX, PDF, EML, EMLX, MSGand other documents with free to use online **[GroupDocs Comparison App](https://products.groupdocs.app/comparison)**.

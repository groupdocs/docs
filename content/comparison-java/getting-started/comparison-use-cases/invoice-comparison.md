---
id: invoice-comparison
url: comparison/java/invoice-comparison
title: Invoice Comparison
weight: 4
description: "You will find how you can use GroupDocs.Comparison for Java inside your production when comparing invoices. Look at file comparison sensitivity configuration and other use cases of the GroupDocs.Comparison API"
keywords: Compare docx files, invoices comparison, how to compare invoices
productName: GroupDocs.Comparison for Java
hideChildren: False
---
# How to Compare Two Invoices

For example, there are two invoices in the DOCX format and you need to compare their contents with the maximum level of detail and comparison sensitivity.

  

| Source Invoice | Target Invoice |
| --- | --- |
| ![](comparison-java/images/invoice-comparison.png)) | ![](comparison-java/images/invoice-comparison_1.png))

[**GroupDocs****.Comparison**](https://products.groupdocs.com/comparison/java) provides the ability to compare two files in DOCX format(or any other [supported file formats]({{< ref "comparison-java/getting-started/supported-document-formats.md" >}})) with adjustment of detalization level and[comparison sensitivity](https://docs.groupdocs.com/display/comparisonjava/Adjusting+comparison+sensitivity).

The following are the steps to compare two DOCX files with specific settings of detalization level and[comparison sensitivity.](Adjusting%2Bcomparison%2Bsensitivity.html)

*   Instantiate [Comparer](https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison/Comparer)objectwith source document path or stream;
*   Call [add](https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison/Comparer#add(java.lang.String))method and specify target document path or stream;
*   Instantiate [CompareOptions](https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison.options/CompareOptions)object with desired [setSensitivityOfComparison](https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison.options/CompareOptions#setSensitivityOfComparison(int)) and [setDetalisationLevel](https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison.options/CompareOptions#setDetalisationLevel(int)) value;
    
*   Call [compare](https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison/Comparer#compare(java.lang.String,%20com.groupdocs.comparison.options.CompareOptions))method and pass [CompareOptions](https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison.options/CompareOptions) object to method.
    

The following code samples demonstrate how to compare two DOCX files.

```csharp
Comparer comparer = new Comparer(SOURCE_FILE);
try {
    comparer.add(TARGET_FILE);
 
    final CompareOptions compareOptions = new CompareOptions();
    compareOptions.setSensitivityOfComparison(100);
    compareOptions.setDetalisationLevel(DetalisationLevel.High);
 
    comparer.compare(RESULT_FILE, compareOptions);
} finally {
    comparer.dispose();
}
```

As a result, we get a DOCX file where the deleted elements are marked in **red**, the added – in **blue**, and the modified – in **green.**

| Result Invoice |
| --- |
| ![](comparison-java/images/invoice-comparison_2.png)) 

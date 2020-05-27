---
id: contracts-comparison
url: comparison/java/contracts-comparison
title: Contracts Comparison
weight: 3
description: "This article describes how to compare contracts, drafts and legal documents using Microsoft Word blacklining feature and GroupDocs.Comparison API."
keywords: Compare contracts, compare drafts, compare blacklining, compare redlining
productName: GroupDocs.Comparison for Java
hideChildren: False
---
# How to Compare Two Contracts 

You have two contracts in DOCX format that were concluded in different years (For example, for 2018 and 2019). You need to check how the conditions have changed after some time. Documents are encrypted, but you know the password from them. You can use the **[GroupDocs.Comparison](https://products.groupdocs.com/comparison/java)** option, enter your password into it and start the file comparison process.

  

| Source File | Target File |
| --- | --- |
| ![](comparison-java/images/contracts-comparison.png)) | ![](comparison-java/images/contracts-comparison_1.png))

[**GroupDocs****.Comparison**](https://products.groupdocs.com/comparison/java) provides the ability to compare two files in DOCX format(or any other [supported file formats]({{< ref "comparison-java/getting-started/supported-document-formats.md" >}})).

The following are the steps to compare two DOCX files

*   Instantiate [LoadOptions](https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison.options.load/LoadOptions)object and specify source document password;
*   Instantiate [Comparer](https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison/Comparer)* object *with source document path or stream and [LoadOptions](https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison.options.load/LoadOptions)object created at previous step;
*   Instantiate another [LoadOptions](https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison.options.load/LoadOptions)object and specify target document password;
*   Call [add](https://apireference.groupdocs.com/net/comparison/groupdocs.comparison/comparer/methods/add/index)method and specify target document path or stream and [LoadOptions](https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison.options.load/LoadOptions)object created at previous step;
*   Call [compare](https://apireference.groupdocs.com/comparison/java/com.groupdocs.comparison/Comparer#compare(java.lang.String))method.

The following code samples demonstrate how to compare two DOCX files.

<table class="confluenceTable"><tbody><tr><td class="confluenceTd"><div class="container" title="Hint: double-click to select code"><div class="line number1 index0 alt2"><code class="java plain">Comparer comparer = </code><code class="java keyword">new</code> <code class="java plain">Comparer(SOURCE_FILE, </code><code class="java keyword">new</code> <code class="java plain">LoadOptions(</code><code class="java string">"source-password"</code><code class="java plain">));</code></div><div class="line number2 index1 alt1"><code class="java keyword">try</code> <code class="java plain">{</code></div><div class="line number3 index2 alt2"><code class="java spaces">&nbsp;&nbsp;&nbsp;&nbsp;</code><code class="java plain">comparer.add(TARGET_FILE, </code><code class="java keyword">new</code> <code class="java plain">LoadOptions(</code><code class="java string">"target-password"</code><code class="java plain">));</code></div><div class="line number4 index3 alt1"><code class="java spaces">&nbsp;&nbsp;&nbsp;&nbsp;</code><code class="java plain">comparer.compare(RESULT_FILE);</code></div><div class="line number5 index4 alt2"><code class="java plain">} </code><code class="java keyword">finally</code> <code class="java plain">{</code></div><div class="line number6 index5 alt1"><code class="java spaces">&nbsp;&nbsp;&nbsp;&nbsp;</code><code class="java plain">comparer.dispose();</code></div><div class="line number7 index6 alt2"><code class="java plain">}</code></div></div></td></tr></tbody></table>

As a result, we get a DOCX file where the deleted elements are marked in **red**, the added – in **blue**, and the modified – in **green.  
**

| Result File |
| --- |
| ![](comparison-java/images/contracts-comparison_2.png)) 

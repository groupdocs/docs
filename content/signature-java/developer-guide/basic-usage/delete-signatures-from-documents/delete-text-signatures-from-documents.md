---
id: delete-text-signatures-from-documents
url: signature/java/delete-text-signatures-from-documents
title: Delete Text signatures from documents
weight: 4
description: "This article explains how to delete Text electronic signatures with GroupDocs.Signature API."
keywords: 
productName: GroupDocs.Signature for Java
hideChildren: False
---
# Delete Text signatures from document

[**GroupDocs.Signature**](https://products.groupdocs.com/signature/java) provides [TextSignature](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature.domain.signatures/TextSignature) class to manipulate text signatures and [delete](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature/Signature#delete(java.io.OutputStream,%20com.groupdocs.signature.domain.signatures.BaseSignature)) them from the documents.   
Please be aware that[delete](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature/Signature#delete(java.io.OutputStream,%20com.groupdocs.signature.domain.signatures.BaseSignature)) method modifies the same document that was passed to constructor of [Signature](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature/Signature) class.

Here are the steps to delete Text signature from the document with GroupDocs.Signature:

*   Create new instance of [Signature](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature/Signature) class and pass source document path as a constructor parameter;
    
*   Instantiate [TextSearchOptions](https://apireference.groupdocs.com/net/signature/groupdocs.signature.options/textsearchoptions) object with desired properties;
    
*   Call [search](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature/Signature#search(java.lang.Class,%20com.groupdocs.signature.options.search.SearchOptions)) method to obtain list of [TextSignatures](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature.domain.signatures/TextSignature);  
    
*   Select from list [TextSignature](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature.domain.signatures/TextSignature) object(s) that should be removed from the document;  
    
*   Call [Signature](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature/Signature) object [delete](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature/Signature#delete(java.io.OutputStream,%20com.groupdocs.signature.domain.signatures.BaseSignature)) method and pass one or several signatures to it.
    

This example shows how to delete Text signature that was found using [search](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature/Signature#search(java.lang.Class,%20com.groupdocs.signature.options.search.SearchOptions)) method.

```csharp
Signature signature = new Signature("signed.pptx");
try
{
    TextSearchOptions options = new TextSearchOptions();
 
    // search for text signatures in document
    List<TextSignature> signatures = signature.search(TextSignature.class,options);
    if(signatures.size() > 0)
    {
        TextSignature textSignature = signatures.get(0);
        boolean result = signature.delete("signed-output.pptx",textSignature);
        if(result)
        {
            System.out.print("Signature with Text " + textSignature.getText() + " was deleted from document [signed-output.pptx].");
        }
        else
        {
            System.out.print("Signature was not deleted from the document! Signature with Text " + textSignature.getText() + " was not found!");
        }
    }
} catch (Exception e) {
    throw new GroupDocsSignatureException(e.getMessage());
}
```

## More resources

### Advanced Usage Topics

To learn more about document eSign features, please refer to the [advanced usage section]({{< ref "signature-java/developer-guide/advanced-usage/_index.md" >}}).

### GitHub Examples 

You may easily run the code above and see the feature in action in our GitHub examples:

*   [GroupDocs.Signature for .NET examples, plugins, and showcase](https://github.com/groupdocs-signature/GroupDocs.Signature-for-.NET)
    
*   [GroupDocs.Signature for Java examples, plugins, and showcase](https://github.com/groupdocs-signature/GroupDocs.Signature-for-Java)
    
*   [Document Signature for .NET MVC UI Example](https://github.com/groupdocs-signature/GroupDocs.Signature-for-.NET-MVC) 
    
*   [Document Signature for .NET App WebForms UI Example](https://github.com/groupdocs-signature/GroupDocs.Signature-for-.NET-WebForms)
    
*   [Document Signature for Java App Dropwizard UI Example](https://github.com/groupdocs-signature/GroupDocs.Signature-for-Java-Dropwizard)
    
*   [Document Signature for Java Spring UI Example](https://github.com/groupdocs-signature/GroupDocs.Signature-for-Java-Spring)
    

### Free Online App 

Along with full-featured .NET library we provide simple, but powerful free Apps.

You are welcome to eSign PDF, Word, Excel, PowerPoint documents with free to use online **[GroupDocs Signature App](https://products.groupdocs.app/signature)**.

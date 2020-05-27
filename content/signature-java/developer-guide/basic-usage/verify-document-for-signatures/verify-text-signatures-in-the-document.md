---
id: verify-text-signatures-in-the-document
url: signature/java/verify-text-signatures-in-the-document
title: Verify Text signatures in the document
weight: 4
description: "This topic explains how to verify Text electronic signatures with GroupDocs.Signature API."
keywords: 
productName: GroupDocs.Signature for Java
hideChildren: False
---
  

# Verify Text signatures in the document

[**GroupDocs.Signature**](https://products.groupdocs.com/signature/java) provides[TextVerifyOptions](https://apireference.groupdocs.com/net/signature/groupdocs.signature.options/textverifyoptions) class to specify different options for verification of Text signatures.

Here are the steps to verify Text signature within the document with GroupDocs.Signature:

*   Create new instance of [Signature](https://apireference.groupdocs.com/net/signature/groupdocs.signature/signature) class and pass source document path as a constructor parameter.
    
*   Instantiate the [TextVerifyOptions](https://apireference.groupdocs.com/net/signature/groupdocs.signature.options/textverifyoptions) object according to your requirements and specify verification options  
    
*   Call [verify](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature/Signature#verify(com.groupdocs.signature.options.verify.VerifyOptions)) method of [Signature](https://apireference.groupdocs.com/net/signature/groupdocs.signature/signature)class instance and pass [TextVerifyOptions](https://apireference.groupdocs.com/net/signature/groupdocs.signature.options/textverifyoptions) to it.
    

  
  

This example shows how to verify Text signature in the document.

```csharp
Signature signature = new Signature("sample.pdf");
TextVerifyOptions options = new TextVerifyOptions();
options.setAllPages(true); // this value is set by default
options.setSignatureImplementation(TextSignatureImplementation.Stamp);
options.setText("John");
options.setMatchType(TextMatchType.Contains);
 
// verify document signatures
VerificationResult result = signature.verify(options);
if (result.isValid())
{
    System.out.print("\nDocument was verified successfully!");
}
else
{
    System.out.print("\nDocument failed verification process.");
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

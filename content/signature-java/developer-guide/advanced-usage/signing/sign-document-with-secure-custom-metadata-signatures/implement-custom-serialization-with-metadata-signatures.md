---
id: implement-custom-serialization-with-metadata-signatures
url: signature/java/implement-custom-serialization-with-metadata-signatures
title: Implement custom serialization with Metadata signatures
weight: 2
description: "This article explains how to implement custom serialization for Metadata electronic signatures."
keywords: 
productName: GroupDocs.Signature for Java
hideChildren: False
---
[**GroupDocs.Signature**](https://products.groupdocs.com/signature/java) provides ability to embed into Metadata signature custom objects. This feature is implemented over object serialization to string and further encryption. By default library uses json format serialization and symmetric encryption but allows to provide custom serialization and encryption. Customization of serialization requires implementation of interface [IDataSerializer](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature.domain.extensions.serialization/IDataSerializer) with two methods to serialize and de-serialize data.

Here are the steps to embed custom object into Metadata signature with GroupDocs.Signature:

*   Implement if needed custom data serialization class that implement [IDataSerializer](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature.domain.extensions.serialization/IDataSerializer) interface. By default GroupDocs.Signature uses embedded json format serialization but allows user to customize it.
    
*   Implement if needed custom data encryption class that implements [IDataEncryption](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature.domain.extensions.encryption/IDataEncryption) interface. By default GroupDocs.Signature has several encryption implementation you can use but allows user to customize it.
*   define class with properties and specify class attributes (like custom serialization attribute, or custom encryption attribute), specify attributes for properties like [FormatAttribute](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature.domain.extensions.serialization/FormatAttribute) to specify serialization name and display format, same as [SkipSerializationAttribute](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature.domain.extensions.serialization/SkipSerializationAttribute) attribute to mark property of class as not serialize   
    
*   Create new instance of [Signature](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature/Signature) class and pass source document path as a constructor parameter
*   Create one or several objects of [MetadataSignature](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature.domain.signatures.metadata/MetadataSignature) object with MetadataSignature[.setValue](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature.domain.signatures.metadata/MetadataSignature#setValue(java.lang.Object)) as object instance. Setup MetadataSignature[.setDataEncryption](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature.domain.signatures.metadata/MetadataSignature#setDataEncryption(com.groupdocs.signature.domain.extensions.encryption.IDataEncryption)) property or use same for [MetadataSignOptions.setDataEncryption](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature.options.sign/MetadataSignOptions#setDataEncryption(com.groupdocs.signature.domain.extensions.encryption.IDataEncryption)) if all signatures should be encrypted.
*   Instantiate the [MetadataSignOptions](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature.options.sign/MetadataSignOptions) object according to your requirements, add all metadata signatures to its collection and setup if needed [setDataEncryption](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature.options.sign/MetadataSignOptions#setDataEncryption(com.groupdocs.signature.domain.extensions.encryption.IDataEncryption)) property,
*   Call [sign](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature/Signature#sign(java.io.OutputStream,%20com.groupdocs.signature.options.sign.SignOptions)) method of [Signature](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature/Signature) class instance and pass [MetadataSignOptions](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature.options.sign/MetadataSignOptions)to it.

  

 This example shows how to specify custom serialization class. This class should be implemented as Attribute and [IDataSerializer](https://apireference.groupdocs.com/net/signature/groupdocs.signature.domain.extensions/idataserializer) interface.

```csharp
public class CustomSerializationAttribute implements IDataSerializer{
 
   public <T> T deserialize(String source, Class<T> type)
   {
       return new Gson().fromJson(source, type);
   }
   public String serialize(Object data)
   {
       return new Gson().toJson(data);
   }
}
```

## Implementation of custom data encryption

This example shows how to specify custom serialization class. This class could be implemented also as Attribute (optional) to specify as class attribute.

```csharp
// Define class that implements IDataEncryption interface
public class CustomXOREncryption implements IDataEncryption
{
    /**
     * <p>
     * Gets or sets non empty key for encryption (at least one character)
     * </p>
     */
    public final int getKey(){ return auto_Key; }
    /**
     * <p>
     * Gets or sets non empty key for encryption (at least one character)
     * </p>
     */
    public final void setKey(int value){ auto_Key = value; }
    private int auto_Key;
 
    /**
     * <p>
     * Encode method to encrypt string.
     * </p>
     * @return Returns enccrypted string
     * @param source Source string to encode.
     */
    public final String encode(String source)
    {
        return process(source);
    }
 
    /**
     * <p>
     * Decode method to obtain decrypted string.
     * </p>
     * @return Returns decrypted string
     * @param source Source string to decode.
     */
    public final String decode(String source)
    {
        return process(source);
    }
 
    /**
     * <p>
     * Using XOR operation get encoded / decoded string
     * </p>
     * @return
     * @param source
     */
    private String process(String source)
    {
        StringBuilder src = new StringBuilder(source);
        StringBuilder dst = new StringBuilder(src.length());
        char chTmp;
        for (int index = 0; index < src.length(); ++index)
        {
            chTmp = src.charAt(index);
            chTmp = (char)(chTmp ^ this.getKey());
            dst.append(chTmp);
        }
        return dst.toString();
    }
}
```

## Definition of class

This example shows how to define custom class with serialization and encryption properties and setup Format attributes for properties.   

```csharp
// define class with custom serialization attribute
public class DocumentSignatureData
{
    public String getID(){ return ID; }
    public void setID(String value){ ID = value; }
    @FormatAttribute(propertyName = "SignID")
    public String ID;
 
 
    public final String getAuthor(){ return Author; }
    public final void setAuthor(String value){ Author = value; }
    @FormatAttribute(propertyName = "SAuth")
    public String Author;
    //JAVA-added public wrapper for internalized property accessor
 
    public final java.util.Date getSigned() {  return Signed; }
    public final void setSigned(java.util.Date value) { Signed = value; }
    @FormatAttribute (propertyName = "SDate",propertyFormat = "yyyy-MM-dd")
    public java.util.Date Signed = new java.util.Date();
 
 
    public final java.math.BigDecimal getDataFactor() { return DataFactor; }
    public final void setDataFactor(java.math.BigDecimal value) { DataFactor = value; }
    @FormatAttribute (propertyName = "SDFact",propertyFormat = "N2")
    public java.math.BigDecimal DataFactor = new java.math.BigDecimal(0.01);
}
```

## Implementation of embedding custom object into Metadata signature

This example shows how to embed custom object into Metadata signature.

```csharp
 Signature signature = new Signature("sample.docx");
 
// create data encryption
IDataEncryption encryption = new CustomXOREncryption();
 
// setup options with text of signature
MetadataSignOptions options = new MetadataSignOptions();
 
// set encryption for all metadata signatures for this options
// if you need separate encryption use own MetadataSignature.DataEncryption property
options.setDataEncryption(encryption);
 
 
// create custom object
DocumentSignatureData documentSignature = new DocumentSignatureData();
documentSignature.setID(java.util.UUID.randomUUID().toString());
documentSignature.setAuthor(System.getenv("USERNAME"));
documentSignature.setSigned(new java.util.Date());
documentSignature.setDataFactor(new java.math.BigDecimal("11.22"));
 
// setup signature metadata
WordProcessingMetadataSignature mdSignature = new WordProcessingMetadataSignature("Signature", documentSignature);
 
// setup signature metadata
WordProcessingMetadataSignature mdAuthor = new WordProcessingMetadataSignature("Author", "Mr.Scherlock Holmes");
 
// setup data of document id
WordProcessingMetadataSignature mdDocId = new WordProcessingMetadataSignature("DocumentId", java.util.UUID.randomUUID().toString());
 
// add signatures to options
options.getSignatures().add(mdSignature);
options.getSignatures().add(mdAuthor);
options.getSignatures().add(mdDocId);
 
// sign document to file
SignResult signResult = signature.sign("MetadataCustomSerializationObject.docx", options);
// analyzing result
System.out.print("List of newly created signatures:");
int number = 1;
for(BaseSignature temp : signResult.getSucceeded())
{
    System.out.print("Signature #"+ number++ +": Type: "+temp.getSignatureType()+" Id:"+temp.getSignatureId()+
            ",Location: "+temp.getLeft()+"x"+temp.getTop()+". Size: "+temp.getWidth()+"x"+temp.getHeight());
}
```

## More resources

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

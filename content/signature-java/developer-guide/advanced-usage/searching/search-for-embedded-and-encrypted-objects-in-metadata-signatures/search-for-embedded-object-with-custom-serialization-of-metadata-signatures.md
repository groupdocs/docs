---
id: search-for-embedded-object-with-custom-serialization-of-metadata-signatures
url: signature/java/search-for-embedded-object-with-custom-serialization-of-metadata-signatures
title: Search for embedded object with custom serialization of Metadata signatures
weight: 2
description: " This article explains how to search for embedded electronic signatures with custom serialization in document metadata. This topic contains example of custom serialization, class definition and search for serialized objects in the document metadata with GroupDocs.Signature."
keywords: 
productName: GroupDocs.Signature for Java
hideChildren: False
---
[**GroupDocs.Signature**](https://products.groupdocs.com/signature/java) provides additional features when searching for Metadata Signatures that were previously encrypted and have embedded data objects. 

*   ability to search for embedded custom objects into metadata and decrypt them to original source values
*   ability to search for encrypted text of metadata signature and decrypt it  
      

Here are the steps to search and decrypt previously encrypted text of metadata and decrypt custom object from metadata signature ([MetadataSignature](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature.domain.signatures.metadata/MetadataSignature)) with GroupDocs.Signature API:

*   Implement custom data serialization class that implement [IDataEncryption](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature.domain.extensions.encryption/IDataEncryption) interface. By default Signature uses embedded json format serialization but allows user to customize it. if object of class was serialized by custom serialization when searching for it, this class should also has same serialization attribute.  
    
*   Implement custom data encryption class that implements [IDataEncryption](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature.domain.extensions.encryption/IDataEncryption) interface. By default Signature has several encryption implementation you can use but allows user to customize it. There's ability to specify inline encryption to use
*   Define class with proper DataSerialization attribute  
    
*   Instantiate the [MetadataSearchOptions](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature.options.search/MetadataSearchOptions) object value 
    
*   Call [search](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature/Signature#search(java.lang.Class,%20com.groupdocs.signature.options.search.SearchOptions)) method of [Signature](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature/Signature)class instance and pass [MetadataSearchOptions](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature.options.search/MetadataSearchOptions) to it.
    
*   Process each Metadata signature and set property [setDataEncryption](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature.domain.signatures.metadata/MetadataSignature#setDataEncryption(com.groupdocs.signature.domain.extensions.encryption.IDataEncryption)) to specify data encryption and call [getData](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature.domain.signatures.metadata/MetadataSignature#getData(java.lang.Class)) method to retrieve object 
    

## Implementation of custom data serialization

 This example shows how to specify custom serialization class. This class should be implemented as Attribute and [IDataSerializer](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature.domain.extensions.serialization/IDataSerializer) interface.

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
public static class DocumentSignatureData
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

  

## Search for embedded custom objects in metadata signatures

 This example shows how to decrypt previously embedded encrypted custom objects into metadata signature. [MetadataSignature](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature.domain.signatures.metadata/MetadataSignature) contains method [getData](https://apireference.groupdocs.com/java/signature/com.groupdocs.signature.domain.signatures.metadata/MetadataSignature#getData(java.lang.Class))to retrieve object

```csharp
Signature signature = new Signature("MetadataCustomSerializationObject.docx");
 
// create data encryption
IDataEncryption encryption = new CustomXOREncryption();
 
MetadataSearchOptions options = new MetadataSearchOptions();
options.setDataEncryption(encryption);
 
// search for signatures in document
List<WordProcessingMetadataSignature> signatures = signature.search(WordProcessingMetadataSignature.class,options);
System.out.print("\nSource document contains following signatures.");
// get required metadata signatures
WordProcessingMetadataSignature wordSignature = null;
for (WordProcessingMetadataSignature mdSign : signatures) {
    if (mdSign.getName().equals("Signature")) {
        wordSignature = mdSign;
        break;
    }
}
if (wordSignature != null)
{
    DocumentSignatureData documentSignatureData = wordSignature.getData(DocumentSignatureData.class);
    if (documentSignatureData != null)
    {
        System.out.print("Signature has DocumentSignatureData object:\n ID = " + documentSignatureData.getID() + ", Author = " + documentSignatureData.getAuthor() + ", Signed = " + documentSignatureData.getSigned() + ", DataFactor " + documentSignatureData.getDataFactor());
    }
}
// get required metadata signatures
WordProcessingMetadataSignature mdAuthor = null;
for (WordProcessingMetadataSignature mdSign : signatures) {
    if (mdSign.getName().equals("Author")) {
        mdAuthor = mdSign;
        break;
    }
}
if (mdAuthor != null)
{
    System.out.print("Metadata signature found. Name : " + mdAuthor.getName() + ". Value: " + mdAuthor.getData(String.class));
}
// get required metadata signatures
WordProcessingMetadataSignature mdDocId = null;
for (WordProcessingMetadataSignature mdSign : signatures) {
    if (mdSign.getName().equals("DocumentId")) {
        mdDocId = mdSign;
        break;
    }
}
if (mdDocId != null)
{
    System.out.print("Metadata signature found. Name : " + mdDocId.getName() + ". Value: " + mdDocId.getData(String.class));
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

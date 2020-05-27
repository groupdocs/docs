---
id: installation
url: redaction/java/installation
title: Installation
weight: 4
description: ""
keywords: 
productName: GroupDocs.Redaction for Java
hideChildren: False
---
GroupDocs hosts all Java APIs on [GroupDocs Repository](https://repository.groupdocs.com/webapp/#/artifacts/browse/tree/General/repo). You can easily use GroupDocs.Redaction for Java API directly in your Maven projects with simple configurations.

### Specify GroupDocs Repository Configuration

First, you need to specify GroupDocs repository configuration/location in your Maven `pom.xml` as follows:

**XML**

```csharp
<repositories>
	<repository>
		<id>GroupDocsJavaAPI</id>
		<name>GroupDocs Java API</name>
		<url>http://repository.groupdocs.com/repo/</url>
	</repository>
</repositories>
```

### Define GroupDocs.Redaction for Java API Dependency

Then define GroupDocs.Redaction for Java API dependency in your `pom.xml` as follows:

**XML**

```csharp
<dependencies>
    <dependency>
        <groupId>com.groupdocs</groupId>
        <artifactId>groupdocs-redaction</artifactId>
        <version>19.10</version> 
    </dependency>
</dependencies>
```

After performing above-mentioned steps, GroupDocs.Redaction for Java dependency will finally be added to your Maven project.

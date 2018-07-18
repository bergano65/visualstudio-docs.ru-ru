---
title: 'CA3075: обработка небезопасных DTD'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 65798d66-7a30-4359-b064-61a8660c1eed
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 821a2a3f50f94808482d50a8e1e36feefb184173
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31922433"
---
# <a name="ca3075-insecure-dtd-processing"></a>CA3075: обработка небезопасных DTD
|||
|-|-|
|TypeName|InsecureDTDProcessing|
|CheckId|CA3075|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 Если вы используете небезопасные экземпляры <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> или ссылаетесь на источники внешних сущностей, средство синтаксического анализа может принять недоверенные входные данные и раскрыть конфиденциальную информацию злоумышленникам.

## <a name="rule-description"></a>Описание правила
 Объект *определения типа документа (DTD)* является одним из двух способов определения допустимости документа, синтаксический анализатор XML в соответствии с определением [World Wide Web Consortium (W3C) языка (XML) 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/). Это правило ищет свойства и экземпляры, в которых принимаются недоверенные данные, для предупреждения разработчиков о возможных угрозах [Information Disclosure](/dotnet/framework/wcf/feature-details/information-disclosure) , которые могут привести к атакам типа [отказ в обслуживании (DoS)](/dotnet/framework/wcf/feature-details/denial-of-service) . Это правило активируется, если:

-   обработка DtdProcessing включена в экземпляре <xref:System.Xml.XmlReader> , который разрешает внешние сущности XML с использованием <xref:System.Xml.XmlUrlResolver>;

-   задано свойство <xref:System.Xml.XmlNode.InnerXml%2A> в XML;

-   <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> свойство задается для синтаксического анализа.

-   недоверенные входные данные обрабатываются с помощью <xref:System.Xml.XmlResolver> вместо <xref:System.Xml.XmlSecureResolver> ;

-   Средство чтения XML.<xref:System.Xml.XmlReader.Create%2A> метод вызывается с небезопасным <xref:System.Xml.XmlReaderSettings> экземпляра или без экземпляра.

-   <xref:System.Xml.XmlReader> будет создано небезопасных параметров или значений.

 В каждом из этих случаев результат одинаковый: содержимое из файловой системы или сетевых папок с компьютера, на котором обрабатывается XML, станет доступно злоумышленнику, что впоследствии можно использовать для атак типа "отказ в обслуживании".

## <a name="how-to-fix-violations"></a>Устранение нарушений

-   Перехватывайте и обрабатывайте все исключения XmlTextReader Exception соответствующим образом, чтобы не допустить раскрытия информации.

-   Используйте <xref:System.Xml.XmlSecureResolver> , чтобы ограничить набор ресурсов, к которым может получить доступ XmlTextReader.

-   Не разрешайте <xref:System.Xml.XmlReader> открывать какие-либо внешние ресурсы, установив для свойства <xref:System.Xml.XmlResolver> значение **NULL**.

-   Убедитесь, что свойство <xref:System.Data.DataViewManager.DataViewSettingCollectionString%2A> <xref:System.Data.DataViewManager> назначено из доверенного источника.

 .NET 3.5 и более ранней версии

-   Отключите обработку DTD при работе с недоверенными источниками, задав для свойства <xref:System.Xml.XmlReaderSettings.ProhibitDtd%2A> значение **true** .

-   Класс XmlTextReader содержит полное требование наследования доверия.

 .NET 4 и более поздней версии

-   Не включайте DtdProcessing при работе с недоверенными источниками, задав <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A?displayProperty=nameWithType> свойства **запретить** или **Ignore**.

-   Убедитесь, что метод Load() принимает экземпляр XmlReader во всех случаях InnerXml.

> [!NOTE]
>  Это правило может ложно срабатывать в некоторых допустимых экземплярах XmlSecureResolver. Исправление этой проблемы будет выпущено ориентировочно в середине 2016 г.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Отключайте правило этого предупреждения, только если уверены, что входные данные получены из доверенного источника.

## <a name="pseudo-code-examples"></a>Примеры псевдокода

### <a name="violation"></a>Нарушение

```csharp
using System.IO;
using System.Xml.Schema;

class TestClass
{
    public XmlSchema Test
    {
        get
        {
            var src = "";
            TextReader tr = new StreamReader(src);
            XmlSchema schema = XmlSchema.Read(tr, null); // warn
            return schema;
        }
    }
}
```

### <a name="solution"></a>Решение

```csharp
using System.IO;
using System.Xml;
using System.Xml.Schema;

class TestClass
{
    public XmlSchema Test
    {
        get
        {
            var src = "";
            TextReader tr = new StreamReader(src);
            XmlTextReader reader = new XmlTextReader(tr) { DtdProcessing = DtdProcessing.Prohibit };
            XmlSchema schema = XmlSchema.Read(reader , null);
            return schema;
        }
    }
}
```

### <a name="violation"></a>Нарушение

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public XmlReaderSettings settings = new XmlReaderSettings();
        public void TestMethod(string path)
        {
            var reader = XmlReader.Create(path, settings);  // warn
        }
    }
}
```

### <a name="solution"></a>Решение

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public XmlReaderSettings settings = new XmlReaderSettings()
        {
            DtdProcessing = DtdProcessing.Prohibit
        };

        public void TestMethod(string path)
        {
            var reader = XmlReader.Create(path, settings);
        }
    }
}
```

### <a name="violations"></a>Нарушения

```csharp
using System.Xml;

namespace TestNamespace
{
    public class DoNotUseSetInnerXml
    {
        public void TestMethod(string xml)
        {
            XmlDocument doc = new XmlDocument() { XmlResolver = null };
            doc.InnerXml = xml; // warn
        }
    }
}
```

```csharp
using System.Xml;

namespace TestNamespace
{
    public class DoNotUseLoadXml
    {
        public void TestMethod(string xml)
        {
            XmlDocument doc = new XmlDocument(){ XmlResolver = null };
            doc.LoadXml(xml); // warn
        }
    }
}
```

### <a name="solution"></a>Решение

```csharp
using System.Xml;

public static void TestMethod(string xml)
{
    XmlDocument doc = new XmlDocument() { XmlResolver = null };
    System.IO.StringReader sreader = new System.IO.StringReader(xml);
    XmlTextReader reader = new XmlTextReader(sreader) { DtdProcessing = DtdProcessing.Prohibit };
    doc.Load(reader);
}
```

### <a name="violation"></a>Нарушение

```csharp
using System.IO;
using System.Xml;
using System.Xml.Serialization;

namespace TestNamespace
{
    public class UseXmlReaderForDeserialize
    {
        public void TestMethod(Stream stream)
        {
            XmlSerializer serializer = new XmlSerializer(typeof(UseXmlReaderForDeserialize));
            serializer.Deserialize(stream); // warn
        }
    }
}
```

### <a name="solution"></a>Решение

```csharp
using System.IO;
using System.Xml;
using System.Xml.Serialization;

namespace TestNamespace
{
    public class UseXmlReaderForDeserialize
    {
        public void TestMethod(Stream stream)
        {
            XmlSerializer serializer = new XmlSerializer(typeof(UseXmlReaderForDeserialize));
            XmlTextReader reader = new XmlTextReader(stream) { DtdProcessing = DtdProcessing.Prohibit } ;
            serializer.Deserialize(reader );
        }
    }
}
```

### <a name="violation"></a>Нарушение

```csharp
using System.Xml;
using System.Xml.XPath;

namespace TestNamespace
{
    public class UseXmlReaderForXPathDocument
    {
        public void TestMethod(string path)
        {
            XPathDocument doc = new XPathDocument(path); // warn
        }
    }
}
```

### <a name="solution"></a>Решение

```csharp
using System.Xml;
using System.Xml.XPath;

namespace TestNamespace
{
    public class UseXmlReaderForXPathDocument
    {
        public void TestMethod(string path)
        {
            XmlTextReader reader = new XmlTextReader(path) { DtdProcessing = DtdProcessing.Prohibit };
            XPathDocument doc = new XPathDocument(reader);
        }
    }
}
```

### <a name="violation"></a>Нарушение

```csharp
using System.Xml;

namespace TestNamespace
{
    class TestClass
    {
        public XmlDocument doc = new XmlDocument() { XmlResolver = new XmlUrlResolver() };
    }
}
```

### <a name="solution"></a>Решение

```csharp
using System.Xml;

namespace TestNamespace
{
    class TestClass
    {
        public XmlDocument doc = new XmlDocument() { XmlResolver = null }; // or set to a XmlSecureResolver instance
    }
}
```

### <a name="violations"></a>Нарушения

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public void TestMethod(string path)
        {
            XmlReaderSettings settings = new XmlReaderSettings(){ DtdProcessing = DtdProcessing.Parse };
            XmlReader reader = XmlReader.Create(path, settings); // warn
        }
    }
}
```

```csharp
using System.Xml;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod()
        {
            var reader = XmlTextReader.Create(""doc.xml""); //warn
        }
    }
}
```

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public void TestMethod(string path)
        {
            try {
                XmlTextReader reader = new XmlTextReader(path); // warn
            }
            catch { throw ; }
            finally {}
        }
    }
}
```

### <a name="solution"></a>Решение

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public void TestMethod(string path)
        {
            XmlReaderSettings settings = new XmlReaderSettings(){ DtdProcessing = DtdProcessing.Prohibit };
            XmlReader reader = XmlReader.Create(path, settings);
        }
    }
}
```
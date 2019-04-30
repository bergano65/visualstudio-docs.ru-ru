---
title: CA3075. Обработка небезопасных DTD
ms.date: 03/18/2019
ms.topic: reference
ms.assetid: 65798d66-7a30-4359-b064-61a8660c1eed
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6de817e3aaecbdd1c89cc2174e91126ea39d99d7
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62541121"
---
# <a name="ca3075-insecure-dtd-processing"></a>CA3075. Обработка небезопасных DTD

|||
|-|-|
|TypeName|InsecureDTDProcessing|
|CheckId|CA3075|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина

Если вы используете небезопасные экземпляры <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> или ссылаетесь на источники внешних сущностей, средство синтаксического анализа может принять недоверенные входные данные и раскрыть конфиденциальную информацию злоумышленникам.

## <a name="rule-description"></a>Описание правила

*DTD* — это один из двух способов определения допустимости документа средством синтаксического анализа XML, как указано в  [стандарте XML 1.0 консорциума W3C](http://www.w3.org/TR/2008/REC-xml-20081126/). Это правило ищет свойства и экземпляры, в которых принимаются недоверенные данные, для предупреждения разработчиков о возможных [раскрытие информации](/dotnet/framework/wcf/feature-details/information-disclosure) угроз или [отказ в обслуживании (DoS)](/dotnet/framework/wcf/feature-details/denial-of-service) атак. Это правило активируется, если:

- обработка DtdProcessing включена в экземпляре <xref:System.Xml.XmlReader> , который разрешает внешние сущности XML с использованием <xref:System.Xml.XmlUrlResolver>;

- задано свойство <xref:System.Xml.XmlNode.InnerXml%2A> в XML;

- <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> свойству присваивается синтаксического анализа.

- Недоверенные входные данные обрабатываются с помощью <xref:System.Xml.XmlResolver> вместо <xref:System.Xml.XmlSecureResolver>.

- <xref:System.Xml.XmlReader.Create%2A?displayProperty=nameWithType> Метод вызывается с небезопасным <xref:System.Xml.XmlReaderSettings> экземпляра или без экземпляра.

- <xref:System.Xml.XmlReader> создается с небезопасные параметры или значения.

В каждом из этих случаев результат будет одинаковым: злоумышленнику будет предоставляться содержимое из любой системы или сети общих папок на компьютере, где обрабатывается XML, или обработка DTD может использоваться как отказ в обслуживании.

## <a name="how-to-fix-violations"></a>Устранение нарушений

- Перехватывайте и обрабатывайте все исключения XmlTextReader Exception соответствующим образом, чтобы не допустить раскрытия информации.

- Используйте <xref:System.Xml.XmlSecureResolver> для ограничения ресурсов, которые может получить доступ XmlTextReader.

- Не разрешайте <xref:System.Xml.XmlReader> открывать какие-либо внешние ресурсы, установив для свойства <xref:System.Xml.XmlResolver> значение **NULL**.

- Убедитесь, что <xref:System.Data.DataViewManager.DataViewSettingCollectionString%2A?displayProperty=nameWithType> свойство назначено из доверенного источника.

**.NET 3.5 и более ранних версий**

- Отключите обработку DTD при работе с недоверенными источниками, задав <xref:System.Xml.XmlReaderSettings.ProhibitDtd%2A> свойства **true**.

- Класс XmlTextReader содержит полное требование наследования доверия.

**.NET 4 и более поздние версии**

- Не включайте dtdprocessing при работе с недоверенными источниками, задав <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A?displayProperty=nameWithType> свойства **запретить** или **пропустить**.

- Убедитесь, что метод Load() принимает экземпляр XmlReader во всех случаях InnerXml.

> [!NOTE]
> Это правило может ложно срабатывать в некоторых допустимых экземплярах XmlSecureResolver.

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
    XmlReader reader = XmlReader.Create(sreader, new XmlReaderSettings() { XmlResolver = null });
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
            XmlReader reader = XmlReader.Create(stream, new XmlReaderSettings() { XmlResolver = null });
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
            XmlReader reader = XmlReader.Create(path, new XmlReaderSettings() { XmlResolver = null });
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
            XmlReaderSettings settings = new XmlReaderSettings() { XmlResolver = null };
            XmlReader reader = XmlReader.Create(path, settings);
        }
    }
}
```

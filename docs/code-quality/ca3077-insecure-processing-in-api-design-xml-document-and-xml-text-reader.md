---
title: CA3077. Небезопасная обработка в структуре API средств чтения документов и текста XML
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
ms.assetid: 7f33771b-f3c8-4c02-bef6-f581b623c303
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 757378a7bcf421cb8d895357628b511ea749f38b
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54999799"
---
# <a name="ca3077-insecure-processing-in-api-design-xml-document-and-xml-text-reader"></a>CA3077. Небезопасная обработка в структуре API средств чтения документов и текста XML

|||
|-|-|
|TypeName|InsecureDTDProcessingInAPIDesign|
|CheckId|CA3077|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 При разработке API, производных от XMLDocument и XMLTextReader, обратите внимание на <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A>.  Использование небезопасных экземпляров DTDProcessing при ссылке на источники внешних сущностей или их разрешении, а также при задании небезопасных значений в XML может привести к раскрытию информации.

## <a name="rule-description"></a>Описание правила
 *DTD* — это один из двух способов определения допустимости документа средством синтаксического анализа XML, как указано в  [стандарте XML 1.0 консорциума W3C](http://www.w3.org/TR/2008/REC-xml-20081126/). Это правило ищет свойства и экземпляры, в которых принимаются недоверенные данные, для предупреждения разработчиков о возможных угрозах [Information Disclosure](/dotnet/framework/wcf/feature-details/information-disclosure) , которые могут привести к атакам типа [отказ в обслуживании (DoS)](/dotnet/framework/wcf/feature-details/denial-of-service) . Это правило активируется, если:

- <xref:System.Xml.XmlDocument> или <xref:System.Xml.XmlTextReader> классы используют значения сопоставителя по умолчанию для обработки DTD.

- конструктор для производных классов XmlDocument или XmlTextReader не определен либо для <xref:System.Xml.XmlResolver>не используется безопасное значение.

## <a name="how-to-fix-violations"></a>Устранение нарушений

- Перехватывайте и обрабатывайте все исключения XmlTextReader Exception соответствующим образом, чтобы не допустить раскрытия информации.

- Используйте <xref:System.Xml.XmlSecureResolver>вместо XmlResolver, чтобы ограничить ресурсы, может получить доступ XmlTextReader.

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Отключайте правило этого предупреждения, только если уверены, что входные данные получены из доверенного источника.

## <a name="pseudo-code-examples"></a>Примеры псевдокода

### <a name="violation"></a>Нарушение

```csharp
using System;
using System.Xml;

namespace TestNamespace
{
    class TestClass : XmlDocument
    {
        public TestClass () {} // warn
    }

    class TestClass2 : XmlTextReader
    {
        public TestClass2() // warn
        {
        }
    }
}
```

### <a name="solution"></a>Решение

```csharp
using System;
using System.Xml;

namespace TestNamespace
{
    class TestClass : XmlDocument
    {
        public TestClass ()
        {
            XmlResolver = null;
        }
    }

    class TestClass2 : XmlTextReader
    {
        public TestClass2()
        {
               XmlResolver = null;
        }
    }
}
```
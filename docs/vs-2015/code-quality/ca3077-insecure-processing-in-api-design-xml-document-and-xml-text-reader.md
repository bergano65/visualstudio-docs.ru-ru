---
title: 'CA3077: Небезопасная обработка в структуре API, XML-документ и средства чтения текста XML | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f33771b-f3c8-4c02-bef6-f581b623c303
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 175d655c2283dfe764564d42b6893b12d1f09e22
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591884"
---
# <a name="ca3077-insecure-processing-in-api-design-xml-document-and-xml-text-reader"></a>CA3077: небезопасная обработка в структуре API средств чтения документов и текста XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [CA3077: обработка небезопасных в структуре API, XML-документ и средства чтения текста XML](https://docs.microsoft.com/visualstudio/code-quality/ca3077-insecure-processing-in-api-design-xml-document-and-xml-text-reader).

|||
|-|-|
|TypeName|InsecureDTDProcessingInAPIDesign|
|CheckId|CA3077|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 При разработке API, производных от XMLDocument и XMLTextReader, обратите внимание на <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A>.  Использование небезопасных экземпляров DTDProcessing при ссылке на источники внешних сущностей или их разрешении, а также при задании небезопасных значений в XML может привести к раскрытию информации.

## <a name="rule-description"></a>Описание правила
 Объект [определения типа документа (DTD)](https://msdn.microsoft.com/library/aa468547.aspx) является одним из двух способов определения допустимости документа, синтаксический анализатор XML в соответствии с определением [World Wide Web Consortium (W3C) XML Extensible Markup Language () 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/). Это правило ищет свойства и экземпляры, в которых принимаются недоверенные данные, для предупреждения разработчиков о возможных [раскрытие информации](http://msdn.microsoft.com/library/4064c89f-afa6-444a-aa7e-807ef072131c) угроз, которые могут привести к [отказ в обслуживании (DoS)](http://msdn.microsoft.com/library/dfb150f3-d598-4697-a5e6-6779e4f9b600) атак. Это правило активируется, если:

-   <xref:System.Xml.XmlDocument> или <xref:System.Xml.XmlTextReader> классы используют значения сопоставителя по умолчанию для обработки DTD.

-   конструктор для производных классов XmlDocument или XmlTextReader не определен либо для <xref:System.Xml.XmlResolver>не используется безопасное значение.

## <a name="how-to-fix-violations"></a>Устранение нарушений

-   Перехватывайте и обрабатывайте все исключения XmlTextReader Exception соответствующим образом, чтобы не допустить раскрытия информации.

-   Используйте <xref:System.Xml.XmlSecureResolver>вместо XmlResolver, чтобы ограничить ресурсы, может получить доступ XmlTextReader.

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




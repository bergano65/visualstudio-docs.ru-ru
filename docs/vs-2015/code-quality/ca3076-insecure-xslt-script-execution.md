---
title: 'CA3076: небезопасное выполнение скрипта XSLT | Документация Майкрософт'
ms.date: 11/15/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 53cb7a46-c564-488f-bc51-0e210a7853c9
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2b3e06bb7a150c4bb07eefc0571818f1127fe460
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545123"
---
# <a name="ca3076-insecure-xslt-script-execution"></a>CA3076. Выполнение небезопасного скрипта XSLT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Элемент|Значение|
|-|-|
|TypeName|InsecureXSLTScriptExecution|
|CheckId|CA3076|
|Категория|Microsoft.Security|
|Критическое изменение|Не критическое|

## <a name="cause"></a>Причина
 При небезопасном выполнении преобразований [XSLT](https://support.microsoft.com/kb/313997) в приложениях .NET процессор может [разрешить ненадежные ссылки URI](https://msdn.microsoft.com/ba3e4d4f-1ee7-4226-a51a-78a1f1b5bd8a) , которые могут раскрыть конфиденциальную информацию злоумышленникам, что приведет к атакам типа "отказ в обслуживании" и межсайтовые атаки.

## <a name="rule-description"></a>Описание правила
 [XSLT](https://msdn.microsoft.com/6377ce5f-3c45-42a6-b7a9-ec8da588b60c) — это стандарт консорциума W3C для преобразования данных XML. XSLT обычно используется для записи таблиц стилей в целях преобразования данных XML в другие форматы, такие как HTML, текст фиксированной длины, текст с разделителями-запятыми или другой формат XML. Хотя эта возможность по умолчанию запрещена, вы можете включить ее для проекта.

 Чтобы предотвратить доступ к уязвимой области, это правило срабатывает при каждом XslCompiledTransform.<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> Получает небезопасные экземпляры сочетаний <xref:System.Xml.Xsl.XsltSettings> и <xref:System.Xml.XmlResolver> , которые позволяют обрабатывать вредоносные скрипты.

## <a name="how-to-fix-violations"></a>Устранение нарушений

- Замените небезопасный аргумент XsltSettings на XsltSettings.<xref:System.Xml.Xsl.XsltSettings.Default%2A> или с экземпляром, который отключил функцию документа и выполнение скрипта.

- Замените аргумент <xref:System.Xml.XmlResolver> на NULL или экземпляр <xref:System.Xml.XmlSecureResolver> .

## <a name="when-to-suppress-warnings"></a>Отключение предупреждений
 Отключайте правило этого предупреждения, только если уверены, что входные данные получены из доверенного источника.

## <a name="pseudo-code-examples"></a>Примеры псевдокода

### <a name="violation"></a>Нарушение

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
         void TestMethod()
        {
             XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
             var settings = XsltSettings.TrustedXslt;
             var resolver = new XmlUrlResolver();
             xslCompiledTransform.Load("testStylesheet", settings, resolver); // warn
        }
    }
} 
```

### <a name="solution"></a>Решение

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        void TestMethod()
        {
            XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
            var settings = XsltSettings.Default;
            var resolver = new XmlUrlResolver();
            xslCompiledTransform.Load("testStylesheet", settings, resolver);
        }
    }
}
```

### <a name="violation"></a>Нарушение

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod(XsltSettings settings)
        {
            try
            {
                XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
                var resolver = new XmlUrlResolver();
                xslCompiledTransform.Load("testStylesheet", settings, resolver); // warn
            }
            catch { throw; }
            finally { }
        }
    }
}
```

### <a name="solution"></a>Решение

```csharp
using System.Xml;
using System.Xml.Xsl;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod(XsltSettings settings)
        {
            try
            {
                XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();
                settings.EnableDocumentFunction = false;
                settings.EnableScript = false;
                var resolver = new XmlUrlResolver();
                xslCompiledTransform.Load("testStylesheet", settings, resolver);
            }
            catch { throw; }
            finally { }
        }
    }
}
```

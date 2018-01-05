---
title: "CA3076: Выполнение небезопасного скрипта XSLT | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53cb7a46-c564-488f-bc51-0e210a7853c9
caps.latest.revision: "5"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 09cf5533bff2eb2254f3ca70d4dea275c9354201
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="ca3076-insecure-xslt-script-execution"></a>CA3076: выполнение небезопасного скрипта XSLT
|||  
|-|-|  
|TypeName|InsecureXSLTScriptExecution|  
|CheckId|CA3076|  
|Категория|Microsoft.Security|  
|Критическое изменение|Не критическое|  
  
## <a name="cause"></a>Причина  
 При выполнении [таблицы стилей преобразования (XSLT)](https://support.microsoft.com/en-us/kb/313997) в приложениях .NET небезопасно, обработчик может разрешить недоверенные ссылки URI, раскрывающие конфиденциальную информацию злоумышленникам, что приведет к Атак отказа в службе и между сайтами.  
  
## <a name="rule-description"></a>Описание правила  
 **XSLT** — это стандарт консорциума World Wide Web (W3C) для преобразования XML-данных. XSLT обычно используется для записи таблиц стилей в целях преобразования данных XML в другие форматы, такие как HTML, текст фиксированной длины, текст с разделителями-запятыми или другой формат XML. Хотя эта возможность по умолчанию запрещена, вы можете включить ее для проекта.  
  
 Чтобы обезопасить вас от атак, это правило активируется каждый раз, когда XslCompiledTransform.<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> получает небезопасную комбинацию экземпляров <xref:System.Xml.Xsl.XsltSettings> и <xref:System.Xml.XmlResolver>, которая допускает обработку вредоносных скриптов.  
  
## <a name="how-to-fix-violations"></a>Устранение нарушений  
  
-   Замените небезопасный аргумент XsltSettings на XsltSettings.<xref:System.Xml.Xsl.XsltSettings.Default%2A> или на экземпляр с отключенными функциями документов и выполнением скриптов.  
  
-   Замените аргумент <xref:System.Xml.XmlResolver> на NULL или экземпляр <xref:System.Xml.XmlSecureResolver> .  
  
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
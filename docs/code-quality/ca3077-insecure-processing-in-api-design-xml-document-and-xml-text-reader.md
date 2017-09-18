---
title: "CA3077: небезопасная обработка в структуре API средств чтения документов и текста XML | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7f33771b-f3c8-4c02-bef6-f581b623c303
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA3077: небезопасная обработка в структуре API средств чтения документов и текста XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|InsecureDTDProcessingInAPIDesign|  
|CheckId|CA3077|  
|Категория|Microsoft.Security|  
|Критическое изменение|Не критическое|  
  
## Причина  
 При разработке API, производных от XMLDocument и XMLTextReader, обратите внимание на <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A>.  Использование небезопасных экземпляров DTDProcessing при ссылке на источники внешних сущностей или их разрешении, а также при задании небезопасных значений в XML может привести к раскрытию информации.  
  
## Описание правила  
 [DTD](https://msdn.microsoft.com/en-us/library/aa468547.aspx) — это один из двух способов определения допустимости документа средством синтаксического анализа XML, как указано в [стандарте XML 1.0 консорциума W3C](http://www.w3.org/TR/2008/REC-xml-20081126/). Это правило ищет свойства и экземпляры, в которых принимаются недоверенные данные, для предупреждения разработчиков о возможных угрозах [Раскрытие информации](../Topic/Information%20Disclosure.md), которые могут привести к атакам типа [отказ в обслуживании \(DoS\)](../Topic/Denial%20of%20Service.md). Это правило активируется, если:  
  
-   классы <xref:System.Xml.XmlDocument> и <xref:System.Xml.XmlTextReader> используют значения сопоставителя по умолчанию для обработки DTD;  
  
-   конструктор для производных классов XmlDocument или XmlTextReader не определен либо для <xref:System.Xml.XmlResolver> не используется безопасное значение.  
  
## Устранение нарушений  
  
-   Перехватывайте и обрабатывайте все исключения XmlTextReader exception соответствующим образом, чтобы не допустить раскрытия информации.  
  
-   Используйте <xref:System.Xml.XmlSecureResolver> вместо XmlResolver, чтобы ограничить доступ к ресурсам для  XmlTextReader.  
  
## Отключение предупреждений  
 Отключайте правило этого предупреждения, только если уверены, что входные данные получены из доверенного источника.  
  
## Примеры псевдокода  
  
### Нарушение  
  
```c#  
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
  
### Решение  
  
```c#  
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
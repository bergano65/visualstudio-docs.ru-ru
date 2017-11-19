---
title: "Как: создание шаблонов из шаблонов с помощью Escape-последовательности | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: text templates, generating templates from templates
ms.assetid: 4126156a-7cea-48b8-925e-7790806cfe6c
caps.latest.revision: "35"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: 421b8a8bde2bb383889bcb58915fa8a3acb027cf
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>Практическое руководство. Создание шаблонов из шаблонов с помощью escape-последовательностей
Можно создать текстовый шаблон, создающий другой текстовый шаблон, сгенерированный текстовый вывод. Чтобы сделать это, необходимо использовать escape-последовательности для разграничения теги текстового шаблона. Если не использовать escape-последовательности, сгенерированный текстовый шаблон будет иметь предопределенное значение. Дополнительные сведения об использовании escape-последовательностей в текстовых шаблонах см. в разделе [с помощью Escape-последовательностей в текстовых шаблонах](../modeling/using-escape-sequences-in-text-templates.md).  
  
### <a name="to-generate-a-text-template-from-within-a-text-template"></a>Создание текстового шаблона из текстового шаблона  
  
-   Используйте обратную косую черту (\\) как escape-символа для создания необходимых тегов разметки в текстовом шаблоне для директив, инструкции, выражения и функции в отдельный текстовый файл шаблона класса.  
  
    ```  
    \<#@ directive \#>  
    \<# statement \#>  
    \<#= expression \#>  
    \<#+ classfeature \#>  
    ```  
  
## <a name="example"></a>Пример  
 В следующем примере escape-символы для создания текстового шаблона из текстового шаблона. `output` Директива задает целевой тип файла для текстового файла шаблона (.tt).  
  
```csharp  
\<#@ output extension=".tt" \#>  
\<#@ assembly name="System.Xml.dll" \#>  
\<#@ import namespace="System.Xml" \#>  
\<#  
XmlDocument xDoc = new XmlDocument();  
//System.Diagnostics.Debugger.Break();  
    xDoc.Load(@"E:\CSharp\Overview.xml");  
    XmlAttributeCollection attributes = xDoc.Attributes;  
    if (attributes != null)  
    {  
       foreach (XmlAttribute attr in attributes)  
       {\#>  
           \<#= attr.Name \#>  
       \<#}  
     }  
\#>  
```  
  
 Сгенерированный текстовый вывод является текстовым шаблоном.  
  
```  
<#@ output extension=".tt" #>  
<#@ assembly name="System.Xml.dll" #>  
<#@ import namespace="System.Xml" #>  
<#  
XmlDocument xDoc = new XmlDocument();  
//System.Diagnostics.Debugger.Break();  
    xDoc.Load(@"E:\CSharp\Overview.xml");  
    XmlAttributeCollection attributes = xDoc.Attributes;  
    if (attributes != null)  
    {  
       foreach (XmlAttribute attr in attributes)  
       {#>  
           <#= attr.Name #>  
       <#}  
     }  
#>  
```
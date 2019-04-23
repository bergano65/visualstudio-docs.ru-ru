---
title: Практическое руководство. Создание шаблонов из шаблонов с помощью escape-последовательности | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, generating templates from templates
ms.assetid: 4126156a-7cea-48b8-925e-7790806cfe6c
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4a3ddd7896732c5b87c5b6bd2032c27fffd96a41
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60109742"
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>Практическое руководство. Создание шаблонов из шаблонов с помощью escape-последовательностей
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно создать текстовый шаблон, создающий другой текстовый шаблон, сгенерированный текстовый вывод. Чтобы сделать это, необходимо использовать escape-последовательности для разграничения тегов текстового шаблона. Если вы не используете escape-последовательности, сгенерированный текстовый шаблон будет иметь предопределенное значение. Дополнительные сведения об использовании escape-последовательностей в текстовых шаблонах см. в разделе [с помощью escape-последовательностей в текстовых шаблонах](../modeling/using-escape-sequences-in-text-templates.md).  
  
### <a name="to-generate-a-text-template-from-within-a-text-template"></a>Для создания текстового шаблона из текстового шаблона  
  
- Используйте обратную косую черту (\\) как escape-символа для создания необходимых тегов разметки в текстовый шаблон для директивы, инструкции, выражения и функции в отдельный текстовый файл шаблона класса.  
  
    ```  
    \<#@ directive \#>  
    \<# statement \#>  
    \<#= expression \#>  
    \<#+ classfeature \#>  
    ```  
  
## <a name="example"></a>Пример  
 В следующем примере escape-символы для создания текстового шаблона из текстового шаблона. `output` Директива задает целевой тип файла для текстового файла шаблона (TT-).  
  
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

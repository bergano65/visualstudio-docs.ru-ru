---
title: Инструкции. Создание шаблонов из шаблонов с помощью escape-последовательностей | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, generating templates from templates
ms.assetid: 4126156a-7cea-48b8-925e-7790806cfe6c
caps.latest.revision: 37
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 501b7f040cb841d19c06ccc8fe7615a5b4a5e70d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657347"
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>Практическое руководство. Создание шаблонов из шаблонов с помощью escape-последовательностей
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно создать текстовый шаблон, который создает другой текстовый шаблон в качестве выходного текста. Для этого необходимо использовать escape-последовательности для отделения тегов текстовых шаблонов. Если вы не используете escape-последовательности, созданный текстовый шаблон будет иметь предварительно определенное значение. Дополнительные сведения об использовании escape-последовательностей в текстовых шаблонах см. [в разделе использование escape-последовательностей в текстовых шаблонах](../modeling/using-escape-sequences-in-text-templates.md).

### <a name="to-generate-a-text-template-from-within-a-text-template"></a>Создание текстового шаблона из текстового шаблона

- Используйте обратную косую черту ( \\ ) в качестве escape-символа для создания необходимых тегов разметки в текстовом шаблоне для директив, инструкций, выражений и функций класса в отдельном файле текстового шаблона.

    ```
    \<#@ directive \#>
    \<# statement \#>
    \<#= expression \#>
    \<#+ classfeature \#>
    ```

## <a name="example"></a>Пример
 В следующем примере escape-символы используются для создания текстового шаблона из текстового шаблона. `output`Директива устанавливает тип файла назначения в тип файла текстового шаблона (. TT).

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

 Созданный текстовый вывод является текстовым шаблоном.

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

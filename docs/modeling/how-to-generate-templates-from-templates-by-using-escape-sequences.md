---
title: Использовать escape-последовательности для создания шаблонов на основе шаблонов
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, generating templates from templates
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7872b9bf55ad5d712ac01edf10c4b9df2a82feea
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263686"
---
# <a name="how-to-generate-templates-from-templates-by-using-escape-sequences"></a>Практическое руководство. Создание шаблонов из шаблонов с помощью escape-последовательностей
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
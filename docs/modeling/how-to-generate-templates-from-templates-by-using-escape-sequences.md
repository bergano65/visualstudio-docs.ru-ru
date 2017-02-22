---
title: "How to: Generate Templates from Templates By Using Escape Sequences | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, generating templates from templates"
ms.assetid: 4126156a-7cea-48b8-925e-7790806cfe6c
caps.latest.revision: 35
caps.handback.revision: 35
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# How to: Generate Templates from Templates By Using Escape Sequences
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Можно создать текстовый шаблон, создающий другой текстовый шаблон, так же, как генерируется текстовый вывод.  Для этого необходимо использовать escape\-последовательности, отмечающие теги текстового шаблона.  Если не использовать escape\-последовательности, сгенерированный текстовый шаблон будет иметь предопределенное значение.  Дополнительные сведения об использовании escape\-последовательностей в текстовых шаблонах см. в разделе [Using Escape Sequences in Text Templates](../modeling/using-escape-sequences-in-text-templates.md).  
  
### Генерирование текстового шаблона из текстового шаблона  
  
-   Используйте в текстовом шаблоне обратную косую черту \(\\\) в качестве escape\-символа для создания необходимых тегов разметки для директив, операторов. выражений и элементов классов в отдельном файле текстового шаблона.  
  
    ```  
    \<#@ directive \#>  
    \<# statement \#>  
    \<#= expression \#>  
    \<#+ classfeature \#>  
    ```  
  
## Пример  
 В следующем примере escape\-символы используются для создания текстового шаблона из текстового шаблона.  Директива `output` устанавливает тип файла назначения как тип файла текстового шаблона \(.tt\).  
  
```c#  
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
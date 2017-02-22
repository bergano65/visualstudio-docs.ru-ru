---
title: "T4 Output Directive | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 03a14993-47ad-4f2e-8032-57db28d5842a
caps.latest.revision: 4
caps.handback.revision: 4
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# T4 Output Directive
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В текстовых шаблонах [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] директива `output` используется для определения расширения файла и кодировки преобразованного файла.  
  
 Например, если ваш проект [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] включает файл шаблона с именем **MyTemplate.tt**, который содержит следующую директиву:  
  
 `<#@output extension=".cs"#>`  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] создаст файл с именем **MyTemplate.cs**.  
  
 Директива `output` не требуется в текстовых шаблонах времени выполнения \(предварительно обработанных\).  Вместо этого приложение получает созданную строку, вызывая `TextTransform()`.  Для получения дополнительной информации см. [Run\-Time Text Generation with T4 Text Templates](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
## Применение директивы output  
  
```  
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>  
```  
  
 В каждом текстовом шаблоне должна быть только одна директива `output`.  
  
## Атрибут extension  
 Указывает расширение файла созданного файла текстового вывода.  
  
 Значение по умолчанию — **.cs**  
  
 Примеры  
 `<#@ output extension=".txt" #>`  
  
 `<#@ output extension=".htm" #>`  
  
 `<#@ output extension=".cs" #>`  
  
 `<#@ output extension=".vb" #>`  
  
 Допустимые значения:  
 любое допустимое расширение файла.  
  
## Атрибут encoding  
 Задает кодировку для использования при создании выходного файла.  Например:  
  
 `<#@ output encoding="utf-8"#>`  
  
 Значение по умолчанию — кодировка, используемая файлом текстового шаблона.  
  
 Допустимые значения:  
 `us-ascii`  
  
 `utf-16BE`  
  
 `utf-16`  
  
 `utf-8`  
  
 `utf-7`  
  
 `utf-32`  
  
 `0` \(системное значение по умолчанию\)  
  
 Как правило, можно использовать строку WebName или число CodePage любых кодировок, возвращаемых <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName>.
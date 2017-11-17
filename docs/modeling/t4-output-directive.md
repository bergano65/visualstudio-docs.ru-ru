---
title: "T4 Директива Output | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03a14993-47ad-4f2e-8032-57db28d5842a
caps.latest.revision: "4"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: bf96406356799a0953ee34eb736266267fe74510
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/27/2017
---
# <a name="t4-output-directive"></a>Директива Output T4
В текстовых шаблонах [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] директива `output` используется для определения расширения файла и кодировки преобразованного файла.  
  
 Например если ваш [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] проект включает файл шаблона с именем **MyTemplate.tt** которого содержит следующую директиву:  
  
 `<#@output extension=".cs"#>`  
  
 затем [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] создаст файл с именем **MyTemplate.cs**  
  
 Директива `output` не требуется в текстовых шаблонах времени выполнения (предварительно обработанных). Вместо этого приложение получает созданную строку, вызывая `TextTransform()`. Дополнительные сведения см. в разделе [Создание текста во время выполнения с помощью текстовых шаблонов T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
## <a name="using-the-output-directive"></a>Применение директивы output  
  
```  
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>  
```  
  
 В каждом текстовом шаблоне должна быть только одна директива `output`.  
  
## <a name="extension-attribute"></a>атрибут расширения  
 Указывает расширение файла созданного файла текстового вывода.  
  
 Значение по умолчанию — **.cs**  
  
 Примеры  
 `<#@ output extension=".txt" #>`  
  
 `<#@ output extension=".htm" #>`  
  
 `<#@ output extension=".cs" #>`  
  
 `<#@ output extension=".vb" #>`  
  
 Допустимые значения:  
 любое допустимое расширение файла.  
  
## <a name="encoding-attribute"></a>атрибут кодировки  
 Задает кодировку для использования при создании выходного файла. Например:  
  
 `<#@ output encoding="utf-8"#>`  
  
 Значение по умолчанию — кодировка, используемая файлом текстового шаблона.  
  
 Допустимые значения:  
 `us-ascii`  
  
 `utf-16BE`  
  
 `utf-16`  
  
 `utf-8`  
  
 `utf-7`  
  
 `utf-32`  
  
 `0` (системное значение по умолчанию)  
  
 Как правило, можно использовать строку WebName или число CodePage любых кодировок, возвращаемых <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName>.
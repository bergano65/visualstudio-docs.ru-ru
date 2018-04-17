---
title: T4 Директива Output | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.technology: vs-ide-modeling
ms.openlocfilehash: 40ade1ec02c940270b3a0540b11e719081f1a6de
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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
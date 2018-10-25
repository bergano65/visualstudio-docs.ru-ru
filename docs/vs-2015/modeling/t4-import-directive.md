---
title: T4 Import-директива | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 713ca975-b9aa-4210-bf6d-b7660f5b193b
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 6fa8f027fbb3418fff47b0459628afb691c8a05a
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49893680"
---
# <a name="t4-import-directive"></a>Директива Import T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

В блоках кода текстового шаблона T4 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] директива `import` позволяет ссылаться на элементы в другом пространстве имен без предоставления полного имени. Она эквивалентна директиве `using` в C# или `imports` в [!INCLUDE[vb_current_short](../includes/vb-current-short-md.md)].  
  
 Общие сведения о создании текстовых шаблонов T4 см. в разделе [написание текстового шаблона T4](../modeling/writing-a-t4-text-template.md).  
  
## <a name="using-the-import-directive"></a>Использование директивы Import  
  
```  
<#@ import namespace="namespace" #>  
```  
  
 В этом примере в коде шаблона можно пропустить явное пространство имен для членов группы System.IO:  
  
```  
<#@ import namespace="System.IO" #>  
<#   
   string fileContent = File.ReadAllText("C:\x.txt"); // System.IO.File  
#>   
The file contains: <#=  fileContent #>  
```  
  
## <a name="standard-imports"></a>Стандартные импорты  
 Следующее пространство имен импортируется автоматически, поэтому для него не нужно создавать директиву импорта:  
  
- `System`  
  
  Кроме того, при использовании пользовательской директивы процессор директив может импортировать некоторые пространства имен автоматически.  
  
  Например, при создании шаблонов для доменного языка (DSL) не требуется создавать директивы импорта для следующих пространств имен:  
  
- `Microsoft.VisualStudio.Modeling`  
  
- Пространство имен DSL  
  
## <a name="see-also"></a>См. также  
 [Директива Assembly T4](../modeling/t4-assembly-directive.md)




---
title: Директива Import T4
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 4017ffc67558f6056cb01bf62c5adf9e7569ad4d
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
ms.locfileid: "31946914"
---
# <a name="t4-import-directive"></a>Директива Import T4

В блоках кода текстового шаблона T4 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] директива `import` позволяет ссылаться на элементы в другом пространстве имен без предоставления полного имени. Она эквивалентна директиве `using` в C# или `imports` в [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)].

 Общие сведения о создании текстовых шаблонов T4. в разделе [написание текстового шаблона T4](../modeling/writing-a-t4-text-template.md).

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

-   `System`

 Кроме того, при использовании пользовательской директивы процессор директив может импортировать некоторые пространства имен автоматически.

 Например, при создании шаблонов для доменного языка (DSL) не требуется создавать директивы импорта для следующих пространств имен:

-   `Microsoft.VisualStudio.Modeling`

-   Пространство имен доменного языка

## <a name="see-also"></a>См. также

- [Директива Assembly T4](../modeling/t4-assembly-directive.md)
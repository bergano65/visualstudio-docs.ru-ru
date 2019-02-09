---
title: Директива Import T4
ms.date: 11/04/2016
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f49ab8d3462877a28cf40aed519b71615b23f8d4
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2019
ms.locfileid: "55914075"
---
# <a name="t4-import-directive"></a>Директива Import T4

В блоках кода текстового шаблона Visual Studio T4 `import` директива позволяет ссылаться на элементы в другом пространстве имен без указания полного имени. Она эквивалентна директиве `using` в C# или `imports` в [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)].

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

- Пространства имен Доменного языка

## <a name="see-also"></a>См. также

- [Директива Assembly T4](../modeling/t4-assembly-directive.md)
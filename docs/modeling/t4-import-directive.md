---
title: Директива Import T4
description: Узнайте, что в текстовом шаблоне Visual Studio T4 Директива import позволяет ссылаться на элементы в другом пространстве имен, не указывая полное имя.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d9eb50261b346d8751a76817d97d59a798d17236
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899661"
---
# <a name="t4-import-directive"></a>Директива Import T4

В блоках кода текстового шаблона T4 Visual Studio `import` директива позволяет ссылаться на элементы в другом пространстве имен, не указывая полное имя. Она эквивалентна директиве `using` в C# или `imports` в [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)].

Общие сведения о написании текстовых шаблонов T4 см. в разделе [написание текстового шаблона T4](../modeling/writing-a-t4-text-template.md).

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

## <a name="see-also"></a>См. также раздел

- [Директива Assembly T4](../modeling/t4-assembly-directive.md)

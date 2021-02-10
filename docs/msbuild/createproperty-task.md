---
title: Задача CreateProperty | Документы Майкрософт
description: Используйте задачу CreateProperty MSBuild для заполнения свойств передаваемыми значениями, что позволяет копировать значения из одного свойства или строки в другое свойство или строку.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#CreateProperty
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CreateProperty task [MSBuild]
- MSBuild, CreateProperty task
ms.assetid: fbc31a88-62d4-43d2-b739-68ef3fac38f5
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6ea412f67629998eab035b8cca79111659ab8a0c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99901375"
---
# <a name="createproperty-task"></a>CreateProperty - задача

Заполняет свойства переданными значениями. Это позволяет копировать значения из одного свойства или строки в другое свойство или строку.

## <a name="attributes"></a>Атрибуты

В следующей таблице приводятся параметры задачи `CreateProperty` .

| Параметр | Описание |
|------------------| - |
| `Value` | Необязательный выходной параметр `String`.<br /><br /> Указывает значение для копирования в новое свойство. |
| `ValueSetByTask` | Необязательный выходной параметр `String`.<br /><br /> Содержит то же значение, что и параметр `Value`. Используйте этот параметр только в том случае, если вы не хотите, чтобы MSBuild задавал выходное свойство при пропуске вложенного целевого объекта из-за актуальных выходных данных. |

## <a name="remarks"></a>Примечания

Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Пример

Следующий пример использует задачу `CreateProperty`, чтобы создать свойство `NewFile` с помощью сочетания значений свойств `SourceFilename` и `SourceFileExtension`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <PropertyGroup>
        <SourceFilename>Module1</SourceFilename>
        <SourceFileExtension>vb</SourceFileExtension>
    </PropertyGroup>

    <Target Name="CreateProperties">

        <CreateProperty
            Value="$(SourceFilename).$(SourceFileExtension)">
            <Output
                TaskParameter="Value"
                PropertyName="NewFile" />
        </CreateProperty>

    </Target>

</Project>
```

После запуска проекта значение свойства `NewFile` равно *Module1.vb*.

## <a name="see-also"></a>См. также

- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
- [Задачи](../msbuild/msbuild-tasks.md)

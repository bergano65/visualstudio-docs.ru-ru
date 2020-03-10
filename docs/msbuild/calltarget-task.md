---
title: Задача CallTarget | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CallTarget task [MSBuild]
- MSBuild, CallTarget task
ms.assetid: bb1fe2c4-4383-436f-8326-c24cc4a46150
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 831153a734fa88c045f7b8397db0a033e53862c7
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634491"
---
# <a name="calltarget-task"></a>CallTarget - задача

Вызывает указанные целевые объекты в файле проекта.

## <a name="task-parameters"></a>Параметры задачи

 В следующей таблице приводятся параметры задачи `CallTarget` .

| Параметр | Описание |
|---------------------------| - |
| `RunEachTargetSeparately` | Необязательный входной параметр `Boolean`.<br /><br /> Если задано значение `true`, модуль MSBuild вызывается однократно для каждого целевого объекта. Если задано значение `false`, модуль MSBuild вызывается однократно для сборки всех целевых объектов. Значение по умолчанию — `false`. |
| `TargetOutputs` | Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Содержит выходные данные всех собранных целевых объектов. |
| `Targets` | Необязательный параметр `String[]`.<br /><br /> Указывает один или несколько целевых объектов для сборки. |
| `UseResultsCache` | Необязательный параметр `Boolean`.<br /><br /> Если задано значение `true`, возвращается кэшированный результат (при его наличии).<br /><br /> **Примечание**. При выполнении задачи MSBuild ее выходные данные кэшируются в области (ProjectFileName, GlobalProperties)[TargetNames] в виде списка элементов сборки. |

## <a name="remarks"></a>Примечания

 Если заданный в `Targets` целевой объект завершается сбоем, а `RunEachTargetSeparately` имеет значение `true`, задача продолжает сборку оставшихся целевых объектов.

 Если вы хотите выполнить сборку целевых объектов по умолчанию, используйте [задачу MSBuild](../msbuild/msbuild-task.md) и задайте для параметра `Projects` значение `$(MSBuildProjectFile)`.

 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Пример

 Приведенный ниже пример вызывается `TargetA` из `CallOtherTargets`.

```xml
<Project DefaultTargets="CallOtherTargets"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <Target Name="CallOtherTargets">
        <CallTarget Targets="TargetA"/>
    </Target>

    <Target Name="TargetA">
        <Message Text="Building TargetA..." />
    </Target>

</Project>
```

## <a name="see-also"></a>См. также

- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
- [Целевые объекты](../msbuild/msbuild-targets.md)

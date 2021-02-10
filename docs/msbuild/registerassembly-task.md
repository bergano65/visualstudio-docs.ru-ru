---
title: Задача RegisterAssembly | Документация Майкрософт
description: Узнайте, как MSBuild использует задачу RegisterAssembly для чтения метаданных в указанной сборке и добавления необходимых записей в реестр.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#RegisterAssembly
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, RegisterAssembly task
- RegisterAssembly task [MSBuild]
ms.assetid: ba5f19ac-6764-4d28-9b79-a86de58f8987
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 55625cb1611fec8ed0e8925a671e43505b96c2b9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931852"
---
# <a name="registerassembly-task"></a>RegisterAssembly - задача

Считывает метаданные указанной сборки и добавляет в реестр необходимые записи, что позволяет COM-клиентам прозрачно создавать классы .NET Framework. Поведение этой задачи близко к поведению [средства регистрации сборок Regasm.exe](/dotnet/framework/tools/regasm-exe-assembly-registration-tool), но не идентично ему.

## <a name="parameters"></a>Параметры

 В следующей таблице приводятся параметры задачи `RegisterAssembly` .

|Параметр|Описание|
|---------------|-----------------|
|`Assemblies`|Обязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]`.<br /><br /> Указывает сборки для регистрации в COM.|
|`AssemblyListFile`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Содержит сведения о состоянии взаимодействия между задачей `RegisterAssembly` и задачей [UnregisterAssembly](../msbuild/unregisterassembly-task.md). Благодаря этим сведениям задача `UnregisterAssembly` не пытается отменить регистрацию для сборки, которую не удалось зарегистрировать в задаче `RegisterAssembly`.|
|`CreateCodeBase`|Необязательный параметр `Boolean`.<br /><br /> Если он имеет значение `true`, то в реестре создается запись codebase, которая указывает путь к файлу сборки, не установленному в глобальном кэше сборок. Не следует указывать этот параметр, если впоследствии вы будете устанавливать регистрируемую сборку в глобальном кэше сборок.|
|`TypeLibFiles`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает библиотеку типов, которую нужно создать из указанной сборки. Создаваемая библиотека типов содержит определения типов, заданные в сборке. Библиотека типов создается только в том случае, если выполняется одно из следующих условий:<br /><br /> — библиотеки типов с таким именем не существует в этом расположении;<br />— библиотека типов существует, но она старше передаваемой сборки.<br /><br /> Если библиотека типов новее, чем передаваемая сборка, то новая библиотека не создается, но сборка будет зарегистрирована.<br /><br /> Если указан этот параметр, он должен иметь такое же количество элементов, как и параметр `Assemblies`, иначе задача завершится сбоем. Если входные данные не указаны, задача по умолчанию использует имя сборки, добавляя к нему расширение *.tlb*.|

## <a name="remarks"></a>Примечания

 Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.TaskExtension>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список этих дополнительных параметров и их описания см. в статье [Базовый класс TaskExtension](../msbuild/taskextension-base-class.md).

## <a name="example"></a>Пример

 В следующем примере задача `RegisterAssembly` регистрирует сборки, определенные в коллекции элементов `MyAssemblies`.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">

    <ItemGroup>
        <MyAssemblies Include="MyAssembly.dll" />
    <ItemGroup>

    <Target Name="RegisterAssemblies">
        <RegisterAssembly
            Assemblies="@(MyAssemblies)" >
    </Target>

</Project>
```

## <a name="see-also"></a>См. также раздел

- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)

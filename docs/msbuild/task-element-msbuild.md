---
title: Элемент Task элемента Target (MSBuild) | Документация Майкрософт
description: Сведения об элементе Task элемента Target MSBuild, позволяющем создать и выполнить экземпляр задачи MSBuild.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Task element [MSBuild]
- <Task> element [MSBuild]
ms.assetid: d82e2485-e5f0-4936-a357-745bacccc299
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a4b8e3cb3acccc2e7ae4c6c2d93353bec79a3690
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966049"
---
# <a name="task-element-of-target-msbuild"></a>Элемент Task элемента Target (MSBuild)

Создает и выполняет экземпляр задачи MSBuild. Имя элемента определяется именем создаваемой задачи.

 \<Project> \<Target>

## <a name="syntax"></a>Синтаксис

```xml
<Task Parameter1="Value1"... ParameterN="ValueN"
    ContinueOnError="WarnAndContinue/true/ErrorAndContinue/ErrorAndStop/false"
    Condition="'String A' == 'String B'" >
    <Output... />
</Task>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты

 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|`Condition`|Необязательный атрибут. Проверяемое условие. Дополнительные сведения см. в разделе [Условия](../msbuild/msbuild-conditions.md).|
|`ContinueOnError`|Необязательный атрибут. Может содержать одно из следующих значений:<br /><br /> -   **WarnAndContinue** или **true**. При сбое задачи последующие задачи в элементе [Target](../msbuild/target-element-msbuild.md) и сборке продолжают выполняться, а все ошибки из задачи рассматриваются как предупреждения.<br />-   **ErrorAndContinue**. При сбое задачи последующие задачи в элементе `Target` и сборке продолжают выполняться, а все ошибки из задачи рассматриваются как ошибки.<br />-   **ErrorAndStop** или **false** (значение по умолчанию). При сбое задачи остальные задачи в элементе `Target` и сборке не выполняются, и считается, что возник сбой всего элемента `Target` и всей сборки.<br /><br /> Версии платформы .NET Framework, предшествовавшие 4.5, поддерживали только значения `true` и `false`.<br /><br /> Дополнительные сведения см. в руководстве по [игнорированию ошибок в задачах](../msbuild/how-to-ignore-errors-in-tasks.md).|
|`Parameter`|Требуется, если класс задачи содержит одно или несколько свойств с атрибутом `[Required]`.<br /><br /> Определяемый пользователем параметр задачи, значением которого является значение параметра. В элементе `Task` может существовать любое число параметров, и каждый атрибут соответствует свойству .NET в классе задачи.|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|[Выходные данные](../msbuild/output-element-msbuild.md)|Сохраняет выходные данные задачи в файле проекта. Задача может содержать нуль и более элементов `Output`.|

### <a name="parent-elements"></a>Родительские элементы

| Элемент | Описание |
| - | - |
| [Цель](../msbuild/target-element-msbuild.md) | Элемент контейнера для задач MSBuild. |

## <a name="remarks"></a>Комментарии

 Элемент `Task` в файле проекта MSBuild создает экземпляр задачи, устанавливает для него свойства и выполняет его. Элемент `Output` сохраняет выходные параметры в свойствах или элементах, которые будут использоваться в другом месте в файле проекта.

 Если в родительском элементе `Target` задачи существуют элементы [OnError](../msbuild/onerror-element-msbuild.md), они будут обрабатываться даже в случае сбоя задачи, когда `ContinueOnError` имеет значение `false`. Дополнительные сведения о задачах см. в разделе [Задачи](../msbuild/msbuild-tasks.md).

## <a name="example"></a>Пример

 Следующий пример кода создает экземпляр класса [задачи Csc](../msbuild/csc-task.md), устанавливает шесть свойств и выполняет задачу. После выполнения значение свойства `OutputAssembly` этого объекта помещается в список элементов с именем `FinalAssemblyName`.

```xml
<Target Name="Compile" DependsOnTarget="Resources" >
    <Csc Sources="@(CSFile)"
          TargetType="library"
          Resources="@(CompiledResources)"
          EmitDebugInformation="$(includeDebugInformation)"
          References="@(Reference)"
          DebugType="$(debuggingType)" >
        <Output TaskParameter="OutputAssembly"
                  ItemName="FinalAssemblyName" />
    </Csc>
</Target>
```

## <a name="see-also"></a>См. также раздел

- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
- [Справочник по схеме файла проекта](../msbuild/msbuild-project-file-schema-reference.md)

---
title: Элемент Task (MSBuild) | Документация Майкрософт
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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac3e966521f77716b999203523e1620fd327b631
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56617149"
---
# <a name="task-element-msbuild"></a>Элемент Task (MSBuild)
Создает и выполняет экземпляр задачи [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Имя элемента определяется именем создаваемой задачи.

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
|`ContinueOnError`|Необязательный атрибут. Может содержать одно из следующих значений:<br /><br /> -   **WarnAndContinue** или **true**. При сбое задачи последующие задачи в элементе [Target](../msbuild/target-element-msbuild.md) и сборке продолжают выполняться, а все ошибки из задачи рассматриваются как предупреждения.<br />-   **ErrorAndContinue**. При сбое задачи последующие задачи в элементе `Target` и сборке продолжают выполняться, а все ошибки из задачи рассматриваются как ошибки.<br />-   **ErrorAndStop** или **false** (значение по умолчанию). При сбое задачи остальные задачи в элементе `Target` и сборке не выполняются, и считается, что возник сбой всего элемента `Target` и всей сборки.<br /><br /> Версии платформы .NET Framework, предшествовавшие 4.5, поддерживали только значения `true` и `false`.<br /><br /> Дополнительные сведения см. в разделе [Как Игнорирование ошибок в задачах](../msbuild/how-to-ignore-errors-in-tasks.md).|
|`Parameter`|Требуется, если класс задачи содержит одно или несколько свойств с атрибутом `[Required]`.<br /><br /> Определяемый пользователем параметр задачи, значением которого является значение параметра. В элементе `Task` может существовать любое число параметров, и каждый атрибут соответствует свойству .NET в классе задачи.|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|[Вывод](../msbuild/output-element-msbuild.md)|Сохраняет выходные данные задачи в файле проекта. Задача может содержать нуль и более элементов `Output`.|

### <a name="parent-elements"></a>Родительские элементы

| Элемент | Описание |
| - | - |
| [Целевой объект](../msbuild/target-element-msbuild.md) | Элемент контейнера для задач [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. |

## <a name="remarks"></a>Примечания
 Элемент `Task` в файле проекта [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] создает экземпляр задачи, устанавливает для него свойства и выполняет его. Элемент `Output` сохраняет выходные параметры в свойствах или элементах, которые будут использоваться в другом месте в файле проекта.

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

## <a name="see-also"></a>См. также
- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
- [Справочник по схеме файла проекта](../msbuild/msbuild-project-file-schema-reference.md)

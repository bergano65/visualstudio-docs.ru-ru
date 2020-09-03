---
title: Элемент UsingTask (MSBuild) | Документация Майкрософт
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
ms.assetid: 49d8741b-f1ea-4470-94fd-a1ac27341a6a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 36644a6b21092361d92dba5f0886eb4198884995
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "78263192"
---
# <a name="task-element-of-usingtask-msbuild"></a>Элемент Task элемента UsingTask (MSBuild)

Содержит данные, передаваемые в `UsingTask` `TaskFactory`. Дополнительные сведения см. в статье [Элемент UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<Project> \<UsingTask> \<Task>
 \<Task>

## <a name="syntax"></a>Синтаксис

```xml
<Task Evaluate="true/false" />
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты

 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|`Evaluate`|Дополнительный логический атрибут.<br /><br /> Если он имеет значение `true`, MSBuild при создании экземпляра задачи оценивает все внутренние элементы и развертывает все элементы и свойства, прежде чем передать данные в `TaskFactory`.|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|Данные|Текст между тегами `Task` отправляется в `TaskFactory` без изменений.|

### <a name="parent-elements"></a>Родительские элементы

| Элемент | Описание |
| - | - |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | Предоставляет способ регистрации задач в MSBuild. Проект может содержать любое число элементов `UsingTask`, включая ноль. |

## <a name="example"></a>Пример

 В следующем примере показано использование элемента `Task` с атрибутом `Evaluate`.

```xml
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">
       <ParameterGroup>
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>
              ...
</ParameterGroup>
       <Task Evaluate="true">
       ... Task factory-specific data ...
       </Task>
</UsingTask>
```

## <a name="see-also"></a>См. также

- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
- [Справочник по схеме файла проекта](../msbuild/msbuild-project-file-schema-reference.md)

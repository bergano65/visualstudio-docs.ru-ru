---
title: Элемент TaskBody (MSBuild) | Документация Майкрософт
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- TaskBody element [MSBuild]
- <TaskBody> element [MSBuild]
ms.assetid: 49d8741b-f1ea-4470-94fd-a1ac27341a6a
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac4e04c1a75fe7afdebc984381e17d7e55913fd4
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594985"
---
# <a name="taskbody-element-msbuild"></a>Элемент TaskBody (MSBuild)
Содержит данные, передаваемые в `UsingTask` `TaskFactory`. Дополнительные сведения см. в статье [Элемент UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<Project> \<UsingTask> \<TaskBody>

## <a name="syntax"></a>Синтаксис

```xml
<TaskBody Evaluate="true/false" />
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
|Data|Текст между тегами `TaskBody` отправляется в `TaskFactory` без изменений.|

### <a name="parent-elements"></a>Родительские элементы

| Элемент | Описание |
| - | - |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | Предоставляет способ регистрации задач в [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Проект может содержать любое число элементов `UsingTask`, включая ноль. |

## <a name="example"></a>Пример
 В следующем примере показано использование элемента `TaskBody` с атрибутом `Evaluate`.

```xml
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">
       <ParameterGroup>
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>
              ...
</ParameterGroup>
       <TaskBody Evaluate="true">
      ... Task factory-specific data ...
       </TaskBody>
</UsingTask>
```

## <a name="see-also"></a>См. также
- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
- [Справочник по схеме файла проекта](../msbuild/msbuild-project-file-schema-reference.md)

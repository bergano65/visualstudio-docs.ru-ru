---
title: Элемент ParameterGroup | Документация Майкрософт
ms.date: 03/13/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <ParameterGroup> element [MSBuild]
- ParameterGroup element [MSBuild]
ms.assetid: c3275e69-a427-4889-bc1d-51bff2c285fa
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8c06b9c530d3fff0fdfa429df633daaa4dde8c52
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "78263088"
---
# <a name="parametergroup-element"></a>Элемент ParameterGroup

Содержит необязательный список параметров, которые будут присутствовать в задаче, созданной `UsingTask` `TaskFactory`. Дополнительные сведения см. в статье [Элемент UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 \<Project> \<UsingTask> \<ParameterGroup>
 \<ParameterGroup>

## <a name="syntax"></a>Синтаксис

```xml
<ParameterGroup />
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты

 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

 Отсутствует.

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|[Параметр](../msbuild/parameter-element.md)|Содержит сведения о конкретном параметре для задачи, созданной `UsingTask` `TaskFactory`. Имя элемента — это имя параметра.|

### <a name="parent-elements"></a>Родительские элементы

| Элемент | Описание |
| - | - |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | Предоставляет способ регистрации задач в MSBuild. Проект может содержать любое число элементов `UsingTask`, включая ноль. |

## <a name="example"></a>Пример

 В следующем примере показано использование элемента `ParameterGroup`.

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

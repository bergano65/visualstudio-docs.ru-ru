---
title: Элемент OnError (MSBuild) | Документация Майкрософт
description: Узнайте, как MSBuild использует элемент OnError для выполнения одного или нескольких целевых объектов, если атрибут ContinueOnError имеет значение false для невыполненной задачи.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#OnError
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- OnError Element [MSBuild]
- <OnError Element [MSBuild]
ms.assetid: 765767d3-ecb7-4cd9-ba1e-d9468964dddc
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 574f49b65f47b4a22240ca68b4d74c90ee580a15
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905343"
---
# <a name="onerror-element-msbuild"></a>Элемент OnError (MSBuild)

Вызывает выполнение одного или нескольких целевых объектов, если атрибут `ContinueOnError` для задачи, завершившейся ошибкой, имеет значение `false`.

 \<Project> \<Target>
 \<OnError>

## <a name="syntax"></a>Синтаксис

```xml
<OnError ExecuteTargets="TargetName"
    Condition="'String A'=='String B'" />
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты

 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|`Condition`|Необязательный атрибут.<br /><br /> Проверяемое условие. Дополнительные сведения см. в разделе [Условия](../msbuild/msbuild-conditions.md).|
|`ExecuteTargets`|Обязательный атрибут.<br /><br /> Целевые объекты, которые следует выполнить при сбое задачи. Если целевых объектов несколько, разделите их точкой с запятой. Если целевых объектов несколько, они выполняются в указанном порядке.|

### <a name="child-elements"></a>Дочерние элементы

 Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

| Элемент | Описание |
| - | - |
| [Цель](../msbuild/target-element-msbuild.md) | Элемент контейнера для задач MSBuild. |

## <a name="remarks"></a>Комментарии

 MSBuild выполняет элемент `OnError`, если любая из задач элемента `Target` при завершении имеет атрибут `ContinueOnError` со значением `ErrorAndStop` (или `false`). Если задача завершается с ошибкой, выполняются целевые объекты, заданные в атрибуте `ExecuteTargets`. Если целевой объект содержит несколько элементов `OnError`, в случае сбоя задачи все элементы `OnError` выполняются последовательно.

 Дополнительные сведения об атрибуте `ContinueOnError` см. в статье [Элемент Task (MSBuild)](../msbuild/task-element-msbuild.md). Дополнительные сведения о целевых объектах см. в статье [Целевые объекты](../msbuild/msbuild-targets.md).

## <a name="example"></a>Пример

 Следующий пример кода выполняет задачи `TaskOne` и `TaskTwo`. Если `TaskOne` завершается ошибкой, MSBuild оценивает элемент `OnError` и выполняет целевой объект `OtherTarget`.

```xml
<Target Name="ThisTarget">
    <TaskOne ContinueOnError="ErrorAndStop">
    </TaskOne>
    <TaskTwo>
    </TaskTwo>
    <OnError ExecuteTargets="OtherTarget" />
</Target>
```

## <a name="see-also"></a>См. также

- [Справочник по схеме файла проекта](../msbuild/msbuild-project-file-schema-reference.md)
- [Целевые объекты](../msbuild/msbuild-targets.md)

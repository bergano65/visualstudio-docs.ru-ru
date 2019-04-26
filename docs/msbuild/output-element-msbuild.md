---
title: Элемент Output (MSBuild) | Документация Майкрософт
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Output
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Output> Element [MSBuild]
- Output Element [MSBuild]
ms.assetid: 34bc7cd1-efd3-4b57-b691-4584eeb6a0e9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb8f7a02183fe34dcd882e23ee7bf8b90f9a2cc6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62963927"
---
# <a name="output-element-msbuild"></a>Элемент Output (MSBuild)
Сохраняет выходные данные задачи в элементах и свойствах.

 \<Project> \<Target> \<Task> \<Output>

## <a name="syntax"></a>Синтаксис

```xml
<Output TaskParameter="Parameter"
    PropertyName="PropertyName"
    Condition = "'String A' == 'String B'" />
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|`TaskParameter`|Обязательный атрибут.<br /><br /> Имя выходного параметра задачи.|
|`PropertyName`|Должен быть задан атрибут `PropertyName` или `ItemName`.<br /><br /> Свойство, которое получает значение от выходного параметра задачи. Проект может ссылаться на это свойство, используя синтаксис $(\<имя_свойства>). В качестве имени для этого свойства можно использовать новое имя свойства или имя, которое уже определено в проекте.<br /><br /> Этот атрибут нельзя использовать вместе с атрибутом `ItemName`.|
|`ItemName`|Должен быть задан атрибут `PropertyName` или `ItemName`.<br /><br /> Элемент, получающий значение от выходного параметра задачи. Проект может ссылаться на этот элемент, используя синтаксис @(\<имя_элемента>). В качестве имени для этого элемента можно использовать новое имя элемента или имя, которое уже определено в проекте. Если это имя существующего элемента, значения выходных параметров добавляются к существующему элементу. <br /><br /> Этот атрибут нельзя использовать вместе с атрибутом `PropertyName`.|
|`Condition`|Необязательный атрибут.<br /><br /> Проверяемое условие. Дополнительные сведения см. в разделе [Условия](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Дочерние элементы
 Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

| Элемент | Описание |
| - | - |
| [Задача](../msbuild/task-element-msbuild.md) | Создает и выполняет экземпляр задачи [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. |

## <a name="example"></a>Пример
 В следующем примере кода представлен элемент `Csc`, выполняемый внутри элемента `Target`. Элементы и свойства, передаваемые в качестве параметров задачи, объявляются за пределами этого сегмента кода. Значение выходного параметра `OutputAssembly` сохраняется в элементе `FinalAssemblyName`, а значение выходного параметра `BuildSucceeded` сохраняется в свойстве `BuildWorked`. Дополнительные сведения см. в разделе [Задачи](../msbuild/msbuild-tasks.md).

```xml
<Target Name="Compile" DependsOnTargets="Resources">
    <Csc  Sources="@(CSFile)"
            TargetType="library"
            Resources="@(CompiledResources)"
            EmitDebugInformation="$(includeDebugInformation)"
            References="@(Reference)"
            DebugType="$(debuggingType)"
            OutputAssembly="$(builtdir)\$(MSBuildProjectName).dll" >
        <Output TaskParameter="OutputAssembly"
                  ItemName="FinalAssemblyName" />
        <Output TaskParameter="BuildSucceeded"
                  PropertyName="BuildWorked" />
    </Csc>
</Target>
```

## <a name="see-also"></a>См. также
- [Справочник по схеме файла проекта](../msbuild/msbuild-project-file-schema-reference.md)
- [Задачи](../msbuild/msbuild-tasks.md)

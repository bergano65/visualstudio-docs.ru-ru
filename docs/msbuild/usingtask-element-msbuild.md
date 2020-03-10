---
title: Элемент UsingTask (MSBuild) | Документация Майкрософт
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#UsingTask
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UsingTask element [MSBuild]
- <UsingTask> element [MSBuild]
ms.assetid: 20247902-9446-4a1f-8253-5c7a17e4fe43
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2d977892956c90fd88ff913b9c9300b0176323a4
ms.sourcegitcommit: 3ed59ce39692124fe61c484df4348c0b9abee9b9
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/04/2020
ms.locfileid: "78263127"
---
# <a name="usingtask-element-msbuild"></a>Элемент UsingTask (MSBuild)

Сопоставляет задачу, на которую указана ссылка в элементе [Задача](../msbuild/task-element-msbuild.md), со сборкой, содержащей реализацию этой задачи.

 \<Project> \<UsingTask>

## <a name="syntax"></a>Синтаксис

```xml
<UsingTask TaskName="TaskName"
    AssemblyName = "AssemblyName"
    TaskFactory = "ClassName"
    Condition="'String A'=='String B'" />
```

> [!NOTE]
> В отличие от свойств и элементов, будет использоваться *первый* элемент `UsingTask`, который применяется к `TaskName`. Чтобы переопределить задачи, нужно определить новый элемент `UsingTask` *перед* существующим.

## <a name="attributes-and-elements"></a>Элементы и атрибуты

 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|`AssemblyName`|Требуется задать либо атрибут `AssemblyName`, либо атрибут `AssemblyFile`.<br /><br /> Имя загружаемой сборки. Атрибут `AssemblyName` принимает сборки со строгими именами, хотя строгое именование не является обязательным. Использование данного атрибута эквивалентно загрузке сборки с помощью метода <xref:System.Reflection.Assembly.Load%2A> в .NET.<br /><br /> Этот атрибут нельзя использовать, если используется атрибут `AssemblyFile`.|
|`AssemblyFile`|Требуется задать либо атрибут `AssemblyName`, либо атрибут `AssemblyFile`.<br /><br /> Путь к файлу сборки. Этот атрибут принимает полные пути или относительного пути. Относительные пути задаются относительно каталога файла проекта или файла целей построения, где объявлен элемент `UsingTask`. Использование данного атрибута эквивалентно загрузке сборки с помощью метода <xref:System.Reflection.Assembly.LoadFrom%2A> в .NET.<br /><br /> Этот атрибут нельзя использовать, если используется атрибут `AssemblyName`.|
|`TaskFactory`|Необязательный атрибут.<br /><br /> Указывает класс в сборке, которая отвечает за создание экземпляров указанного имени `Task`.  Пользователь также может указать `Task` в качестве дочернего элемента, который фабрика задач получает и использует для создания задачи. Содержимое `Task` зависит от фабрики задач.|
|`TaskName`|Обязательный атрибут.<br /><br /> Имя задачи для ссылки из сборки. Если возможны неоднозначности, этот атрибут должен всегда указывать полные пространства имен. При наличии неоднозначностей MSBuild выбирает произвольное соответствие, которое может привести к непредвиденным результатам.|
|`Condition`|Необязательный атрибут.<br /><br /> Проверяемое условие. Дополнительные сведения см. в разделе [Условия](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|[ParameterGroup](../msbuild/parametergroup-element.md)|Набор параметров, которые отображаются в задаче, создаваемой с помощью указанного `TaskFactory`.|
|[Задача](../msbuild/task-element-msbuild.md)|Данные, передаваемые в `TaskFactory` для создания экземпляра задачи.|

### <a name="parent-elements"></a>Родительские элементы

| Элемент | Описание |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Обязательный корневой элемент файла проекта MSBuild. |

## <a name="remarks"></a>Примечания

 На переменные среды, свойства командной строки, свойства и элементы уровня проекта можно ссылаться в элементах `UsingTask`, включенных в файл проекта либо напрямую, либо через импортированный файл проекта. Дополнительные сведения см. в разделе [Задачи](../msbuild/msbuild-tasks.md).

> [!NOTE]
> Свойства и элементы уровня проекта не имеют смысла, если элемент`UsingTask` получен из одного из файлов *TASKS*, зарегистрированных глобально в модуле MSBuild. Значения уровня проекта не являются глобальными по отношению к MSBuild.

 В MSBuild 4.0 задачи можно загрузить из файлов *OVERRIDETASK*.

## <a name="example"></a>Пример

 В следующем примере показано использование элемента `UsingTask` с атрибутом `AssemblyName`.

```xml
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">
       <ParameterGroup>
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>
              ...
</ParameterGroup>
       <Task>
      ... Task factory-specific data ...
       </Task>
</UsingTask>
```

## <a name="example"></a>Пример

 В следующем примере показано использование элемента `UsingTask` с атрибутом `AssemblyFile`.

```xml
<UsingTask TaskName="Email"
              AssemblyFile="c:\myTasks\myTask.dll" />
```

## <a name="see-also"></a>См. также

- [Задачи](../msbuild/msbuild-tasks.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
- [Справочник по схеме файла проекта](../msbuild/msbuild-project-file-schema-reference.md)

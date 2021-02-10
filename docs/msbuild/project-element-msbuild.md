---
title: Элемент Project (MSBuild) | Документы Майкрософт
description: Сведения об элементе Project MSBuild, который является обязательным корневым элементом файла проекта MSBuild.
ms.custom: SEO-VS-2020
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Project
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- ToolsVersion attribute [MSBuild]
- <Project> element [MSBuild]
- Project element [MSBuild]
ms.assetid: d1cda56a-dbef-4109-9201-39e962e3f653
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c4aa00df0a1a0b622040a3f808515b9a62fc8f66
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99918838"
---
# <a name="project-element-msbuild"></a>Элемент Project (MSBuild)

Обязательный корневой элемент файла проекта MSBuild.

## <a name="syntax"></a>Синтаксис

```xml
<Project InitialTargets="TargetA;TargetB"
         DefaultTargets="TargetC;TargetD"
         TreatAsLocalProperty="PropertyA;PropertyB"
         ToolsVersion=<version number>
         Sdk="name[/version]"
         xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Sdk... />
    <Choose>... </Choose>
    <PropertyGroup>... </PropertyGroup>
    <ItemGroup>... </ItemGroup>
    <Target>... </Target>
    <UsingTask.../>
    <ProjectExtensions>... </ProjectExtensions>
    <Import... />
</Project>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты

 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

| Атрибут | Описание |
|------------------------| - |
| `DefaultTargets` | Необязательный атрибут.<br /><br /> Целевой объект или объекты по умолчанию служат точкой входа сборки, если целевой объект не указан. Несколько целевых объектов разделяются точкой с запятой (;).<br /><br /> Если целевой объект по умолчанию не указан в атрибуте `DefaultTargets` или командной строке MSBuild, обработчик выполняет первый целевой объект в файл проекта после вычисления элементов [Импорт](../msbuild/import-element-msbuild.md). |
| `InitialTargets` | Необязательный атрибут.<br /><br /> Исходный целевой объект или объекты, выполняемые до целевых объектов, заданных в атрибуте `DefaultTargets` или в командной строке. Несколько целевых объектов разделяются точкой с запятой (`;`). Если несколько импортированных файлов определяют `InitialTargets`, все упомянутые целевые объекты будут выполняться в том порядке, в котором встречаются операции импорта. |
| `Sdk` | Необязательный атрибут. <br /><br /> Имя и (необязательно) версия пакета SDK для создания неявных операторов import, которые добавляются в PROJ-файл. Если версия не указана, MSBuild будет пытаться использовать версию по умолчанию.  Например, `<Project Sdk="Microsoft.NET.Sdk" />` или `<Project Sdk="My.Custom.Sdk/1.0.0" />`. |
| `ToolsVersion` | Необязательный атрибут.<br /><br /> Версия набора инструментов MSBuild используется для определения значений $(MSBuildBinPath) и $(MSBuildToolsPath). |
| `TreatAsLocalProperty` | Необязательный атрибут.<br /><br /> Имена свойств, которые не будут относиться к глобальным. Этот атрибут запрещает определенным свойствам командной строки переопределять значения свойств, заданные в файле проекта или целевых объектов и всех последующих операциях импорта. Несколько свойств разделяются точкой с запятой (;).<br /><br /> Как правило, глобальные свойства переопределяют значения свойств, заданных в файле проекта или целевых объектов. Если свойство указано в значении `TreatAsLocalProperty`, значение глобального свойства не переопределяет значения свойств, заданные в этом файле и всех последующих операциях импорта. Дополнительные сведения см. в [практическом руководстве по сборке одинаковых исходных файлов с различными параметрами](../msbuild/how-to-build-the-same-source-files-with-different-options.md). **Примечание.**  Чтобы задать глобальные свойства из командной строки, используйте параметр **-property** (или **-p**). Кроме того, вы можете задать или изменить глобальные свойства для дочерних проектов в сборках нескольких проектов, используя атрибут `Properties` задачи MSBuild. Дополнительные сведения см. в разделе [Задача MSBuild](../msbuild/msbuild-task.md). |
| `xmlns` | Необязательный атрибут.<br /><br /> Если он указан, атрибут `xmlns` должен иметь значение `http://schemas.microsoft.com/developer/msbuild/2003`. |

### <a name="child-elements"></a>Дочерние элементы

| Элемент | Описание |
| - | - |
| [Choose](../msbuild/choose-element-msbuild.md) | Необязательный элемент.<br /><br /> Вычисляет дочерние элементы для выбора одного набора элементов `ItemGroup` и/или элементов `PropertyGroup` для вычисления. |
| [Импорт](../msbuild/import-element-msbuild.md) | Необязательный элемент.<br /><br /> Позволяет файлу проекта импортировать другой файл проекта. Проект может содержать любое число элементов `Import`, включая ноль. |
| [ImportGroup](../msbuild/importgroup-element.md) | Необязательный элемент.<br /><br /> Содержит коллекцию элементов `Import`, сгруппированных по необязательному условию. |
| [ItemGroup](../msbuild/itemgroup-element-msbuild.md) | Необязательный элемент.<br /><br /> Группирующий элемент для отдельных элементов. Элементы указываются с помощью элемента [Item](../msbuild/item-element-msbuild.md). Проект может содержать любое число элементов `ItemGroup`, включая ноль. |
| [ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md) | Необязательный элемент.<br /><br /> Позволяет определить набор определений элементов, которые представляют собой значения метаданных, по умолчанию применяемых ко всем элементам проекта. Элемент ItemDefinitionGroup используется вместо задач `CreateItem` и `CreateProperty`. |
| [ProjectExtensions](../msbuild/projectextensions-element-msbuild.md) | Необязательный элемент.<br /><br /> Предоставляет способ сохранения данных, не относящихся к MSBuild, в файле проекта MSBuild. Проект может содержать один элемент `ProjectExtensions` или ни одного такого элемента. |
| [PropertyGroup](../msbuild/propertygroup-element-msbuild.md) | Необязательный элемент.<br /><br /> Группирующий элемент для отдельных свойств. Свойства задаются с помощью элемента [Property](../msbuild/property-element-msbuild.md). Проект может содержать любое число элементов `PropertyGroup`, включая ноль. |
| [Sdk](../msbuild/sdk-element-msbuild.md) | Необязательный элемент.<br /><br /> Ссылки на пакет SDK проекта MSBuild.  Этот элемент может использоваться в качестве альтернативы атрибуту Sdk. |
| [Цель](../msbuild/target-element-msbuild.md) | Необязательный элемент.<br /><br /> Содержит набор задач для MSBuild для последовательного выполнения. Задачи указываются с помощью элемента [Task](../msbuild/task-element-msbuild.md). Проект может содержать любое число элементов `Target`, включая ноль. |
| [UsingTask](../msbuild/usingtask-element-msbuild.md) | Необязательный элемент.<br /><br /> Предоставляет способ регистрации задач в MSBuild. Проект может содержать любое число элементов `UsingTask`, включая ноль. |

### <a name="parent-elements"></a>Родительские элементы

 Нет.

## <a name="see-also"></a>См. также раздел

- [Практическое руководство. Выбор цели для первой сборки](../msbuild/how-to-specify-which-target-to-build-first.md)
- [Справочник по командной строке](../msbuild/msbuild-command-line-reference.md)
- [Справочник по схеме файла проекта](../msbuild/msbuild-project-file-schema-reference.md)
- [MSBuild](../msbuild/msbuild.md)

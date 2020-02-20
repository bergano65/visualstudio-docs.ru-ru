---
title: Элемент Project (MSBuild) | Документы Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
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
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b11449626050c4da75b09f2d348a4b1b0190ec4d
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/20/2020
ms.locfileid: "77476935"
---
# <a name="project-element-msbuild"></a>Элемент Project (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Обязательный корневой элемент файла проекта [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)].  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<Project InitialTargets="TargetA;TargetB"  
         DefaultTargets="TargetC;TargetD"  
         TreatAsLocalProperty="PropertyA;PropertyB"  
         ToolsVersion=<version number>  
         xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <Choose>... </Choose>  
    <PropertyGroup>... </PropertyGroup>  
    <ItemGroup>... </ItemGroup>  
    <Target>... </Target>  
    <UsingTask.../>  
    <ProjectExtensions>... </ProjectExtensions>  
    <Import... />  
</Project>  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|       attribute        |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                              Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
|------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    `DefaultTargets`    |                                                                                                                                                                                                                                                                                                 Необязательный атрибут.<br /><br /> Целевой объект или объекты по умолчанию служат точкой входа сборки, если целевой объект не указан. Несколько целевых объектов разделяются точкой с запятой (;).<br /><br /> Если целевой объект по умолчанию не указан в атрибуте `DefaultTargets` или командной строке [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], обработчик выполняет первый целевой объект в файл проекта после вычисления элементов [Импорт](../msbuild/import-element-msbuild.md).                                                                                                                                                                                                                                                                                                  |
|    `InitialTargets`    |                                                                                                                                                                                                                                                                                                                                                                                                                                             Необязательный атрибут.<br /><br /> Исходный целевой объект или объекты, выполняемые до целевых объектов, заданных в атрибуте `DefaultTargets` или в командной строке. Несколько целевых объектов разделяются точкой с запятой (;).                                                                                                                                                                                                                                                                                                                                                                                                                                              |
|     `ToolsVersion`     |                                                                                                                                                                                                                                                                                                                                                                                                                                                                             Необязательный атрибут.<br /><br /> Версия набора инструментов MSBuild используется для определения значений $(MSBuildBinPath) и $(MSBuildToolsPath).                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| `TreatAsLocalProperty` | Необязательный атрибут.<br /><br /> Имена свойств, которые не будут относиться к глобальным. Этот атрибут запрещает определенным свойствам командной строки переопределять значения свойств, заданные в файле проекта или целевых объектов и всех последующих операциях импорта. Несколько свойств разделяются точкой с запятой (;).<br /><br /> Как правило, глобальные свойства переопределяют значения свойств, заданных в файле проекта или целевых объектов. Если свойство указано в значении `TreatAsLocalProperty`, значение глобального свойства не переопределяет значения свойств, заданные в этом файле и всех последующих операциях импорта. Дополнительные сведения см. в разделе [Практическое руководство. Сборка одинаковых исходных файлов с различными параметрами](../msbuild/how-to-build-the-same-source-files-with-different-options.md). **Примечание**. Чтобы задать глобальные свойства из командной строки, используйте параметр **/property** (или **/p**). Кроме того, вы можете задать или изменить глобальные свойства для дочерних проектов в сборках нескольких проектов, используя атрибут `Properties` задачи MSBuild. Дополнительные сведения см. в разделе [Задача MSBuild](../msbuild/msbuild-task.md). |
|        `Xmlns`         |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 Обязательный атрибут (в MSBuild 15. x и более ранних версиях).<br /><br /> Атрибут `xmlns` должен иметь значение `http://schemas.microsoft.com/developer/msbuild/2003`.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Description|  
|-------------|-----------------|  
|[Choose](../msbuild/choose-element-msbuild.md)|Необязательный элемент.<br /><br /> Вычисляет дочерние элементы для выбора одного набора элементов `ItemGroup` и/или элементов `PropertyGroup` для вычисления.|  
|[Импорт](../msbuild/import-element-msbuild.md)|Необязательный элемент.<br /><br /> Позволяет файлу проекта импортировать другой файл проекта. Проект может содержать любое число элементов `Import`, включая ноль.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Необязательный элемент.<br /><br /> Группирующий элемент для отдельных элементов. Элементы указываются с помощью элемента [Item](../msbuild/item-element-msbuild.md). Проект может содержать любое число элементов `ItemGroup`, включая ноль.|  
|[ProjectExtensions](../msbuild/projectextensions-element-msbuild.md)|Необязательный элемент.<br /><br /> Предоставляет способ сохранения данные, не относящихся к [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)], в файле проекта [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Проект может содержать один элемент `ProjectExtensions` или ни одного такого элемента.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Необязательный элемент.<br /><br /> Группирующий элемент для отдельных свойств. Свойства задаются с помощью элемента [Property](../msbuild/property-element-msbuild.md). Проект может содержать любое число элементов `PropertyGroup`, включая ноль.|  
|[Цель](../msbuild/target-element-msbuild.md)|Необязательный элемент.<br /><br /> Содержит набор задач для [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] для последовательного выполнения. Задачи указываются с помощью элемента [Task](../msbuild/task-element-msbuild.md). Проект может содержать любое число элементов `Target`, включая ноль.|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|Необязательный элемент.<br /><br /> Предоставляет способ регистрации задач в [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)]. Проект может содержать любое число элементов `UsingTask`, включая ноль.|  
  
### <a name="parent-elements"></a>Родительские элементы  
 Нет.  
  
## <a name="see-also"></a>См. также:  
 [Практическое руководство. Выбор цели для первой сборки](../msbuild/how-to-specify-which-target-to-build-first.md)   
 [Справочник по командной строке](../msbuild/msbuild-command-line-reference.md)   
 [Справочник по схеме файла проекта](../msbuild/msbuild-project-file-schema-reference.md)   
 [MSBuild](msbuild.md)

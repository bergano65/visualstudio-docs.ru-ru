---
title: "Элемент Project (MSBuild) | Документы Майкрософт"
ms.custom: 
ms.date: 03/13/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 31
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: 203e1e27cc892e96b103fc6cb22a73672a8e16af
ms.openlocfilehash: 224371f6915258a9860c5f05554445f6b1ae106c
ms.lasthandoff: 03/01/2017

---
# <a name="project-element-msbuild"></a>Элемент Project (MSBuild)
Обязательный корневой элемент файла проекта [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  

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

|Атрибут|Описание|  
|---------------|-----------------|  
|`DefaultTargets`|Необязательный атрибут.<br /><br /> Целевой объект или объекты по умолчанию служат точкой входа сборки, если целевой объект не указан. Несколько целевых объектов разделяются точкой с запятой (;).<br /><br /> Если целевой объект по умолчанию не указан в атрибуте `DefaultTargets` или командной строке [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], обработчик выполняет первый целевой объект в файл проекта после вычисления элементов [Импорт](../msbuild/import-element-msbuild.md).|  
|`InitialTargets`|Необязательный атрибут.<br /><br /> Исходный целевой объект или объекты, выполняемые до целевых объектов, заданных в атрибуте `DefaultTargets` или в командной строке. Несколько целевых объектов разделяются точкой с запятой (;).|  
|`SDK`|Необязательный атрибут. (Доступен только для проектов .NET Core в Visual Studio 2017 или более поздних версиях.)<br /><br /> Версия пакета SDK для создания неявных операторов import, которые добавляются в PROJ-файл. Например, `<Project Sdk="Microsoft.NET.Sdk/1.0.0-RC" />`.|  
|`ToolsVersion`|Необязательный атрибут.<br /><br /> Версия набора инструментов MSBuild используется для определения значений $(MSBuildBinPath) и $(MSBuildToolsPath).|  
|`TreatAsLocalProperty`|Необязательный атрибут.<br /><br /> Имена свойств, которые не будут относиться к глобальным. Этот атрибут запрещает определенным свойствам командной строки переопределять значения свойств, заданные в файле проекта или целевых объектов и всех последующих операциях импорта. Несколько свойств разделяются точкой с запятой (;).<br /><br /> Как правило, глобальные свойства переопределяют значения свойств, заданных в файле проекта или целевых объектов. Если свойство указано в значении `TreatAsLocalProperty`, значение глобального свойства не переопределяет значения свойств, заданные в этом файле и всех последующих операциях импорта. Дополнительные сведения см. в разделе [Практическое руководство. Сборка одинаковых исходных файлов с различными параметрами](../msbuild/how-to-build-the-same-source-files-with-different-options.md). **Примечание**. Чтобы задать глобальные свойства из командной строки, используйте параметр **/property** (или **/p**). Кроме того, вы можете задать или изменить глобальные свойства для дочерних проектов в сборках нескольких проектов, используя атрибут `Properties` задачи MSBuild. Дополнительные сведения см. в разделе [Задача MSBuild](../msbuild/msbuild-task.md).|  
|`Xmlns`|Необязательный атрибут.<br /><br /> Если указан, атрибут `xmlns` должен иметь значение "http://schemas.microsoft.com/developer/msbuild/2003".|  

### <a name="child-elements"></a>Дочерние элементы  

|Элемент|Описание|  
|-------------|-----------------|  
|[Choose](../msbuild/choose-element-msbuild.md)|Необязательный элемент.<br /><br /> Вычисляет дочерние элементы для выбора одного набора элементов `ItemGroup` и/или элементов `PropertyGroup` для вычисления.|  
|[Import](../msbuild/import-element-msbuild.md)|Необязательный элемент.<br /><br /> Позволяет файлу проекта импортировать другой файл проекта. Проект может содержать любое число элементов `Import`, включая ноль.|  
|[ItemGroup](../msbuild/itemgroup-element-msbuild.md)|Необязательный элемент.<br /><br /> Группирующий элемент для отдельных элементов. Элементы указываются с помощью элемента [Item](../msbuild/item-element-msbuild.md). Проект может содержать любое число элементов `ItemGroup`, включая ноль.|  
|[ProjectExtensions](../msbuild/projectextensions-element-msbuild.md)|Необязательный элемент.<br /><br /> Предоставляет способ сохранения данные, не относящихся к [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)], в файле проекта [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Проект может содержать один элемент `ProjectExtensions` или ни одного такого элемента.|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|Необязательный элемент.<br /><br /> Группирующий элемент для отдельных свойств. Свойства задаются с помощью элемента [Property](../msbuild/property-element-msbuild.md). Проект может содержать любое число элементов `PropertyGroup`, включая ноль.|  
|[Target](../msbuild/target-element-msbuild.md)|Необязательный элемент.<br /><br /> Содержит набор задач для [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] для последовательного выполнения. Задачи указываются с помощью элемента [Task](../msbuild/task-element-msbuild.md). Проект может содержать любое число элементов `Target`, включая ноль.|  
|[UsingTask](../msbuild/usingtask-element-msbuild.md)|Необязательный элемент.<br /><br /> Предоставляет способ регистрации задач в [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. Проект может содержать любое число элементов `UsingTask`, включая ноль.|  

### <a name="parent-elements"></a>Родительские элементы  
 Отсутствует.  

## <a name="see-also"></a>См. также  
 [Практическое руководство. Выбор цели для первой сборки](../msbuild/how-to-specify-which-target-to-build-first.md)   
 [Справочник по командной строке](../msbuild/msbuild-command-line-reference.md)   
 [Справочник по схеме файла проекта](../msbuild/msbuild-project-file-schema-reference.md)   
 [MSBuild](../msbuild/msbuild.md)


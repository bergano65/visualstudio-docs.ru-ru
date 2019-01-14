---
title: Элемент Import (MSBuild) | Документация Майкрософт
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Import
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Import element [MSBuild]
- <Import> element [MSBuild]
ms.assetid: 3bfecaf1-69fd-4008-b651-c9dafd4389d9
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e6318674d82ffb10839d801df4fc89da94545981
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53900877"
---
# <a name="import-element-msbuild"></a>Элемент Import (MSBuild)
Импортирует содержимое одного файла проекта в другой файл проекта.  

 \<Project>  
 \<Import>  

## <a name="syntax"></a>Синтаксис  

```xml  
<Import Project="ProjectPath"  
    Condition="'String A'=='String B'" />  
```  

## <a name="attributes-and-elements"></a>Элементы и атрибуты  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  

### <a name="attributes"></a>Атрибуты  

|Атрибут|Описание|  
|---------------|-----------------|  
|`Project`|Обязательный атрибут.<br /><br /> Путь к импортируемому файлу проекта. Этот путь может содержать подстановочные знаки. Совпадающие файлы импортируются в отсортированном порядке. С помощью этой функции можно добавить код в проект, просто добавив файл кода в каталог.|  
|`Condition`|Необязательный атрибут.<br /><br /> Проверяемое условие. Дополнительные сведения см. в разделе [Условия](../msbuild/msbuild-conditions.md).|  

### <a name="child-elements"></a>Дочерние элементы  
 Нет  

### <a name="parent-elements"></a>Родительские элементы  

| Элемент | Описание |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Обязательный корневой элемент файла проекта [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] . |
| [ImportGroup](../msbuild/importgroup-element.md) | Содержит коллекцию элементов `Import` , сгруппированных по необязательному условию. |

## <a name="remarks"></a>Примечания  
 С помощью элемента `Import` можно повторно использовать код, который является общим для нескольких файлов проекта. Это упрощает обслуживание кода, так как все изменения, внесенные в общий код, распространяются по всем проектам, которые его импортируют.  

 По соглашению общие импортируемые файлы проекта сохраняются с расширением *TARGETS*, но являются стандартными файлами проекта [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)]. [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] не запрещает импортировать проект с другим расширением файла, однако в целях согласованности рекомендуется использовать расширение *TARGETS*.  

 Относительные пути в импортируемых проектах интерпретируются относительно каталога импортируемого проекта. Таким образом, если файл проекта импортируется в несколько файлов проектов, находящихся в разных расположениях, относительные пути в импортируемом файле проекта будут интерпретироваться по-разному для каждого импортируемого проекта.  

 Всем зарезервированным свойствам [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] , относящимся к файлу проекта, например `MSBuildProjectDirectory` и `MSBuildProjectFile`, на которые имеются ссылки в импортируемом проекте, значения присваиваются в зависимости от импортируемого файла проекта.  

 Если у импортируемого проекта нет атрибута `DefaultTargets` , импортируемые проекты проверяются в порядке импорта и используется значение первого обнаруженного атрибута `DefaultTargets` . Например, если ProjectA импортирует ProjectB и ProjectC (в таком порядке), а ProjectB импортирует ProjectD, [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] сначала ищет `DefaultTargets` в ProjectA, затем в ProjectB, затем в ProjectD и наконец в ProjectC.  

 Схема импортируемого проекта идентична схеме стандартного проекта. Хотя [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] может быть в состоянии выполнить сборку импортируемого проекта, это маловероятно, так как импортируемый проект обычно не содержит сведения о задании свойств или порядке выполнения целевых объектов. В отношении получения этих сведений импортируемый проект зависит от проекта, в который он импортируется.  

> [!NOTE]
>  Хотя операторы условного импорта работают в MSBuilds в командной строке, они не работают с MSBuild в интегрированной среде разработки (IDE) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Проверка условных импортов выполняется с использованием значений конфигурации и платформы, задаваемых при загрузке проекта. Если впоследствии вносятся изменения, требующие перепроверки условий в файле проекта, например изменение платформы, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] повторяет проверку условий для свойств и элементов, но не для импортов. Поскольку условия импорта не перепроверяются, импорт пропускается.  
> 
>  Чтобы обойти это, поместите условные импорты в файлы *TARGETS* или поместите код в условный блок, например [Элемент Choose (MSBuild)](../msbuild/choose-element-msbuild.md).  

## <a name="wildcards"></a>Знаки подстановки  
 В .NET Framework 4 MSBuild позволяет использовать в атрибуте Project подстановочные знаки. При наличии подстановочных знаков все найденные совпадения сортируются (для обеспечения повторяемости), а затем импортируются в полученном порядке, как если бы он был задан явно.  

 Это удобно, если вы хотите предложить точку расширяемости, чтобы кто-то еще мог импортировать файл без явного добавления вами имени файла в импортируемый файл. Для этого *Microsoft.Common.Targets* содержит следующую строку в начале файла.  

```xml  
<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore\*" Condition="'$(ImportByWildcardBeforeMicrosoftCommonTargets)' == 'true' and exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore')"/>  
```  

## <a name="example"></a>Пример  
 В следующем примере показан проект, который содержит несколько элементов и свойств и импортирует общий файл проекта.  

```xml  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  

    <PropertyGroup>  
        <resourcefile>Strings.resx</resourcefile>  

        <compiledresources>  
            $(O)\$(MSBuildProjectName).Strings.resources  
        </compiledresources>  
    </PropertyGroup>  

    <ItemGroup>  
        <CSFile Include="*.cs" />  

        <Reference Include="System" />  
        <Reference Include="System.Data" />  
    </ItemGroup>  

    <Import Project="$(CommonLocation)\General.targets" />  
</Project>  
```  

## <a name="see-also"></a>См. также  
 [Справочник по схеме файла проекта](../msbuild/msbuild-project-file-schema-reference.md)   
 [Практическое руководство. Использование одного целевого объекта в нескольких файлах проектов](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)

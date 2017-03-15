---
title: "С помощью платформы управляемых пакетов для типа проекта (C#) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: d5bc147592bfc36247c35f23ac2885055d096af3
ms.openlocfilehash: 1d70a70b942b3722ed61e1e8a2f2e54d96b916e4
ms.lasthandoff: 02/22/2017

---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>Использование платформа управляемых пакетов для реализации типа проекта (C#)
Управляемые пакета Framework Являющиеся классы C# можно использовать или наследовать реализовать собственные типы проектов. MPF реализует множество интерфейсов, Visual Studio ожидает, что тип проекта, чтобы указать, позволяя пользователю сосредоточиться на реализации особенностей данного типа проекта.  
  
## <a name="using-the-mpf-project-source-code"></a>Используя исходный код проекта MPF  
 Платформа управляемых пакетов для проектов (MPFProj) предоставляет вспомогательные классы для создания и управления новой системы проектов. В отличие от других классов в MPF классы проекта не включаются в сборках, поставляемых с Visual Studio. Вместо этого классы проекта предоставляются в виде исходного кода в [MPF проектов 2013](http://mpfproj12.codeplex.com).  
  
 Чтобы добавить этот проект в решении VSPackage, выполните следующие действия:  
  
1.  Загрузите файлы MPFProj *MPFProjectDir*.  
  
2.  В *MPFProjectDir*\Dev10\Src\CSharp\ProjectBase.file, измените следующий блок:  
  
```  
<!-- Provide a default value for $(ProjectBasePath) -->  
  <PropertyGroup>  
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>  
  </PropertyGroup>  
```  
  
1.  Создайте проект VSPackage.  
  
2.  Выгрузите проект VSPackage.  
  
3.  Измените CSPROJ-файл VSPackage, добавив следующий блок до другой `<Import>` блоков:  
  
```  
<Import Project="MPFProjectDir\Dev10\Src\CSharp\ProjectBase.files" />  
  <PropertyGroup>  
    <!--To specify a different registry root to register your package, uncomment the TargetRegistryRoot tag and specify a registry root in it.  
    <TargetRegistryRoot></TargetRegistryRoot>-->  
    <RegisterOutputPackage>true</RegisterOutputPackage>  
    <RegisterWithCodebase>true</RegisterWithCodebase>  
  </PropertyGroup>  
```  
  
1.  Сохраните проект.  
  
2.  Закройте и снова откройте решение VSPackage.  
  
3.  Снова откройте проект VSPackage. Вы должны увидеть новый каталог с именем ProjectBase.  
  
4.  Добавьте следующие ссылки в проект VSPackage.  
  
     Microsoft.Build.Tasks.4.0  
  
5.  Выполните построение проекта.  
  
## <a name="hierarchy-classes"></a>Иерархия классов  
 В следующей таблице перечислены классы MPFProj, поддерживающие иерархии проекта. Дополнительные сведения см. в разделе [иерархий и выбора](../../extensibility/internals/hierarchies-and-selection.md).  
  
|Имя класса|  
|----------------|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|  
|`Microsoft.VisualStudio.Package.ProjectNode`|  
|`Microsoft.VisualStudio.Package.ProjectContainerNode`|  
|`Microsoft.VisualStudio.Package.FileNode`|  
|`Microsoft.VisualStudio.Package.FolderNode`|  
|`Microsoft.VisualStudio.Package.ReferenceContainerNode`|  
|`Microsoft.VisualStudio.Package.ReferenceNode`|  
|`Microsoft.VisualStudio.Package.ProjectReferenceNode`|  
|`Microsoft.VisualStudio.Package.ComReferenceNode`|  
|`Microsoft.VisualStudio.Package.AssemblyReferenceNode`|  
|`Microsoft.VisualStudio.Package.BuildDependency`|  
  
## <a name="document-handling-classes"></a>Классы для работы с документами  
 Ниже перечислены классы MPF, поддерживающие обработку документов. Дополнительные сведения см. в разделе [Открытие и сохранение элементов проекта](../../extensibility/internals/opening-and-saving-project-items.md).  
  
|Имя класса|  
|----------------|  
|`Microsoft.VisualStudio.Package.DocumentManager`|  
|`Microsoft.VisualStudio.Package.FileDocumentManager`|  
  
## <a name="configuration-and-output-classes"></a>Конфигурация и классы вывода  
 Ниже перечислены классы в MPF, позволяющих типы проектов, которые поддерживают несколько конфигураций, например, отладки и выпуска и коллекции выходных данных проекта. Дополнительные сведения см. в разделе [управление параметры конфигурации](../../extensibility/internals/managing-configuration-options.md).  
  
|Имя класса|  
|----------------|  
|`Microsoft.VisualStudio.Package.ConfigProvider`|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|  
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|  
|`Microsoft.VisualStudio.Package.OutputGroup`|  
|`Microsoft.VisualStudio.Package.ProjectElement`|  
  
## <a name="automation-support-classes"></a>Классы поддержки автоматизации  
 Ниже перечислены классы MPF, поддерживающих автоматизацию, чтобы пользователи типом проекта можно создавать надстройки.  
  
|Имя класса|  
|----------------|  
|`Microsoft.VisualStudio.Package.Automation.OAProject`|  
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|  
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|  
  
## <a name="properties-classes"></a>Свойства классов  
 В следующей таблице перечислены классы в MPF, позволяющих типы проектов добавить свойства, пользователи могут выполнять и изменять в обозревателе свойств.  
  
|Имя класса|  
|----------------|  
|`Microsoft.VisualStudio.Package.LocalizableProperties`|  
|`Microsoft.VisualStudio.Package.NodeProperties`|  
|`Microsoft.VisualStudio.Package.FileNodeProperties`|  
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|  
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|  
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|

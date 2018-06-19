---
title: С помощью платформы управляемых пакетов для типа проекта (C#) | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 112988f28728d40509a3af0360246a6bb4caef1a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31140207"
---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>С помощью платформы управляемых пакетов для реализации типа проекта (C#)
Managed Package Framework (MPF) предоставляет классов C# можно использовать или наследовать для реализации собственных типов проектов. MPF реализует множество интерфейсов, Visual Studio ожидает тип проекта для предоставления, позволяя пользователю сосредоточиться на реализации особенностей типа проекта.  
  
## <a name="using-the-mpf-project-source-code"></a>С помощью MPF исходный код проекта  
 Managed Package Framework для проектов (MPFProj) предоставляет вспомогательные классы для создания и управления новую систему проектов. В отличие от других классов в MPF классы проекта не включаются в сборках, поставляемых с Visual Studio. Вместо этого проект классы предоставляются в виде исходного кода в [MPF для проектов 2013](http://mpfproj12.codeplex.com).  
  
 Добавление этого проекта в решение VSPackage, выполните следующие действия.  
  
1.  Загрузки файлов MPFProj *MPFProjectDir*.  
  
2.  В *MPFProjectDir*\Dev10\Src\CSharp\ProjectBase.file, измените следующий блок:  
  
```  
<!-- Provide a default value for $(ProjectBasePath) -->  
  <PropertyGroup>  
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>  
  </PropertyGroup>  
```  
  
1.  Создайте проект VSPackage.  
  
2.  Выгрузите проект VSPackage.  
  
3.  Измените CSPROJ-файл пакета VSPackage, добавив следующий блок раньше `<Import>` блоки:  
  
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
  
3.  Снова откройте проект VSPackage. Вы увидите новый каталог с именем ProjectBase.  
  
4.  Добавьте следующую ссылку на проект VSPackage.  
  
     Microsoft.Build.Tasks.4.0  
  
5.  Выполните построение проекта.  
  
## <a name="hierarchy-classes"></a>Иерархия классов  
 В следующей таблице перечислены классы в MPFProj, которые поддерживают иерархии проекта. Дополнительные сведения см. в разделе [иерархии и выбора](../../extensibility/internals/hierarchies-and-selection.md).  
  
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
 В следующей таблице перечислены классы MPF, поддерживающие обработку документов. Дополнительные сведения см. в разделе [открытия и сохранения элементов проекта](../../extensibility/internals/opening-and-saving-project-items.md).  
  
|Имя класса|  
|----------------|  
|`Microsoft.VisualStudio.Package.DocumentManager`|  
|`Microsoft.VisualStudio.Package.FileDocumentManager`|  
  
## <a name="configuration-and-output-classes"></a>Конфигурация и классы вывода  
 В следующей таблице перечислены классы MPF, позволяющих типы проектов, которые поддерживают несколько конфигураций, например, отладки и выпуска и коллекциях выходных данных проекта. Дополнительные сведения см. в разделе [управление параметры конфигурации](../../extensibility/internals/managing-configuration-options.md).  
  
|Имя класса|  
|----------------|  
|`Microsoft.VisualStudio.Package.ConfigProvider`|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|  
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|  
|`Microsoft.VisualStudio.Package.OutputGroup`|  
|`Microsoft.VisualStudio.Package.ProjectElement`|  
  
## <a name="automation-support-classes"></a>Классы поддержки автоматизации  
 Ниже перечислены классы MPF, поддерживающих автоматизацию, чтобы пользователи вашего проекта типа можно создавать надстройки.  
  
|Имя класса|  
|----------------|  
|`Microsoft.VisualStudio.Package.Automation.OAProject`|  
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|  
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|  
  
## <a name="properties-classes"></a>Классы, свойства  
 В следующей таблице перечислены классы MPF, позволяющих типы проектов добавить свойства, просмотра и изменения в браузере свойств пользователей.  
  
|Имя класса|  
|----------------|  
|`Microsoft.VisualStudio.Package.LocalizableProperties`|  
|`Microsoft.VisualStudio.Package.NodeProperties`|  
|`Microsoft.VisualStudio.Package.FileNodeProperties`|  
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|  
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|  
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|
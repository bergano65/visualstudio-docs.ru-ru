---
title: Использование платформы управляемых пакетов для реализации типа проекта (C#) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 066695c6d94603d0a0474243ed05dece4cc0bd1f
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300369"
---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>Использование платформы управляемых пакетов для реализации типа проекта (C#)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Платформа управляемых пакетов (MPF) предоставляет C# классы, которые можно использовать или наследовать от, чтобы реализовать собственные типы проектов. В MPF реализовано множество интерфейсов, которые Visual Studio предполагает предоставить для предоставления типа проекта, и вы можете сосредоточиться на реализации конкретных типов проектов.  
  
## <a name="using-the-mpf-project-source-code"></a>Использование исходного кода проекта MPF  
 Платформа управляемых пакетов для проектов (Мпфпрож) предоставляет вспомогательные классы для создания новой системы проектов и управления ею. В отличие от других классов в MPF, классы проектов не включаются в сборки, поставляемые с Visual Studio. Вместо этого классы проектов предоставляются в виде исходного кода по адресу [MPF для проектов 2013](https://archive.codeplex.com/?p=mpfproj12).  
  
 Чтобы добавить этот проект в решение VSPackage, выполните следующие действия.  
  
1. Скачайте файлы Мпфпрож в *мпфпрожектдир*.  
  
2. В *мпфпрожектдир*\Dev10\Src\CSharp\ProjectBase.File измените следующий блок:  
  
```  
<!-- Provide a default value for $(ProjectBasePath) -->  
  <PropertyGroup>  
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>  
  </PropertyGroup>  
```  
  
1. Создайте проект VSPackage.  
  
2. Выгрузить проект VSPackage.  
  
3. Измените файл VSPackage. csproj, добавив следующий блок перед другими блоками `<Import>`:  
  
```  
<Import Project="MPFProjectDir\Dev10\Src\CSharp\ProjectBase.files" />  
  <PropertyGroup>  
    <!--To specify a different registry root to register your package, uncomment the TargetRegistryRoot tag and specify a registry root in it.  
    <TargetRegistryRoot></TargetRegistryRoot>-->  
    <RegisterOutputPackage>true</RegisterOutputPackage>  
    <RegisterWithCodebase>true</RegisterWithCodebase>  
  </PropertyGroup>  
```  
  
1. Сохраните проект.  
  
2. Закройте и снова откройте решение VSPackage.  
  
3. Повторно откройте проект VSPackage. Вы увидите новый каталог с именем Прожектбасе.  
  
4. Добавьте следующую ссылку в проект VSPackage:  
  
     Microsoft. Build. Tasks. 4.0  
  
5. Выполните построение проекта.  
  
## <a name="hierarchy-classes"></a>Классы иерархий  
 В следующей таблице перечислены классы в Мпфпрож, которые поддерживают иерархии проектов. Дополнительные сведения см. в разделе [иерархии и выбор](../../extensibility/internals/hierarchies-and-selection.md).  
  
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
  
## <a name="document-handling-classes"></a>Классы обработки документов  
 В следующей таблице перечислены классы в MPF, поддерживающие обработку документов. Дополнительные сведения см. в разделе [Открытие и сохранение элементов проекта](../../extensibility/internals/opening-and-saving-project-items.md).  
  
|Имя класса|  
|----------------|  
|`Microsoft.VisualStudio.Package.DocumentManager`|  
|`Microsoft.VisualStudio.Package.FileDocumentManager`|  
  
## <a name="configuration-and-output-classes"></a>Классы конфигурации и выходных данных  
 В следующей таблице перечислены классы в MPF, которые позволяют типам проектов поддерживать несколько конфигураций, таких как отладка и выпуск, а также коллекции выходных данных проекта. Дополнительные сведения см. в разделе [Управление параметрами конфигурации](../../extensibility/internals/managing-configuration-options.md).  
  
|Имя класса|  
|----------------|  
|`Microsoft.VisualStudio.Package.ConfigProvider`|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|  
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|  
|`Microsoft.VisualStudio.Package.OutputGroup`|  
|`Microsoft.VisualStudio.Package.ProjectElement`|  
  
## <a name="automation-support-classes"></a>Классы поддержки службы автоматизации  
 В следующей таблице перечислены классы в MPF, поддерживающие автоматизацию, чтобы пользователи типа проекта могли создавать надстройки.  
  
|Имя класса|  
|----------------|  
|`Microsoft.VisualStudio.Package.Automation.OAProject`|  
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|  
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|  
  
## <a name="properties-classes"></a>Классы свойств  
 В следующей таблице перечислены классы в MPF, которые позволяют типам проектов добавлять свойства, которые пользователи могут просматривать и изменять в обозревателе свойств.  
  
|Имя класса|  
|----------------|  
|`Microsoft.VisualStudio.Package.LocalizableProperties`|  
|`Microsoft.VisualStudio.Package.NodeProperties`|  
|`Microsoft.VisualStudio.Package.FileNodeProperties`|  
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|  
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|  
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|

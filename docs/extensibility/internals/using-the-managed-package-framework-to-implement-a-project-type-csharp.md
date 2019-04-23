---
title: С помощью Managed Package Framework для типа проекта (C#) | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8f233e2256fc4baef9ee6ca7f07d3d7b71b68b47
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60112309"
---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>Использование платформы управляемых пакетов для реализации типа проекта (C#)
Managed Package Framework (MPF) предоставляет классы C# можно использовать или наследование для реализации собственных типов проектов. MPF реализует множество интерфейсов, Visual Studio ожидает, что тип проекта для предоставления, позволяя сосредоточиться на реализации особенностей типа проекта.

## <a name="using-the-mpf-project-source-code"></a>С помощью MPF исходному коду проекта
 Managed Package Framework для проектов (MPFProj) предоставляет вспомогательные классы для создания и управления новую систему проектов. В отличие от других классов в MPF классы проекта не включаются в сборки, поставляемые вместе с Visual Studio. Вместо этого классы проекта предоставляются в виде исходного кода на [MPF для проектов 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Чтобы добавить этот проект в решение VSPackage, сделайте следующее:

1. Загрузки файлов MPFProj *MPFProjectDir*.

2. В *MPFProjectDir*\Dev10\Src\CSharp\ProjectBase.file, измените следующий блок:

```
<!-- Provide a default value for $(ProjectBasePath) -->
  <PropertyGroup>
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>
  </PropertyGroup>
```

1. Создайте проект VSPackage.

2. Выгрузите проект VSPackage.

3. Измените CSPROJ-файл пакета VSPackage, добавив следующий блок перед другими `<Import>` блоков:

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

3. Снова откройте проект VSPackage. Вы должны увидеть новый каталог с именем ProjectBase.

4. Добавьте следующую ссылку в проект VSPackage:

     Microsoft.Build.Tasks.4.0

5. Выполните построение проекта.

## <a name="hierarchy-classes"></a>Иерархия классов
 В следующей таблице перечислены классы MPFProj, которые поддерживают иерархии проекта. Дополнительные сведения см. в разделе [иерархии и выбор](../../extensibility/internals/hierarchies-and-selection.md).

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
 Ниже перечислены классы MPF, которые поддерживают обработку документов. Дополнительные сведения см. в разделе [Открытие и сохранение элементов проекта](../../extensibility/internals/opening-and-saving-project-items.md).

|Имя класса|
|----------------|
|`Microsoft.VisualStudio.Package.DocumentManager`|
|`Microsoft.VisualStudio.Package.FileDocumentManager`|

## <a name="configuration-and-output-classes"></a>Конфигурация и классы вывода
 В следующей таблице перечислены классы MPF, с помощью которых типы проектов, которые поддерживают несколько конфигураций, например отладки и выпуска и коллекциях выходных данных проекта. Дополнительные сведения см. в разделе [управление параметры конфигурации](../../extensibility/internals/managing-configuration-options.md).

|Имя класса|
|----------------|
|`Microsoft.VisualStudio.Package.ConfigProvider`|
|`Microsoft.VisualStudio.Package.ProjectConfig`|
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|
|`Microsoft.VisualStudio.Package.OutputGroup`|
|`Microsoft.VisualStudio.Package.ProjectElement`|

## <a name="automation-support-classes"></a>Поддержка модели автоматизации классы
 Ниже перечислены классы MPF, поддерживающих автоматизацию, чтобы пользователи вашего типа проекта можно писать надстройки.

|Имя класса|
|----------------|
|`Microsoft.VisualStudio.Package.Automation.OAProject`|
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|

## <a name="properties-classes"></a>Классы свойства
 В следующей таблице перечислены классы MPF, с помощью которых типы проектов добавить свойства, что пользователи смогут просматривать и изменять в обозревателе свойств.

|Имя класса|
|----------------|
|`Microsoft.VisualStudio.Package.LocalizableProperties`|
|`Microsoft.VisualStudio.Package.NodeProperties`|
|`Microsoft.VisualStudio.Package.FileNodeProperties`|
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|
---
title: Использование рамочной программы управляемого пакета для типа проекта (C) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7ca9dda0b699e0f70b0c945ab9ecfe9f9f4dcda6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704125"
---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>Использование платформы управляемых пакетов для реализации типа проекта (C#)
Рамочная программа управляемых пакетов (MPF) предоставляет классы C,s, которые можно использовать или наследовать для реализации собственных типов проектов. MPF реализует многие интерфейсы Visual Studio ожидает, что тип проекта обеспечит, оставляя вас свободнымсосредоточиться сосредоточиться на реализации особенностей вашего типа проекта.

## <a name="using-the-mpf-project-source-code"></a>Использование кода исходного кода проекта MPF
 Рамочная программа управляемого пакета для проектов (MPFProj) обеспечивает классы помощников для создания и управления новой системой проектов. В отличие от других классов в MPF, классы проектов не включены в сборки, поставляемые visual Studio. Вместо этого классы проектов предоставляются в качестве исходного кода на [MPF для проектов 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Чтобы добавить этот проект в решение VSPackage, сделайте следующее:

1. Скачать файлы MPFProj на *MPFProjectDir*.

2. В *MPFProjectDir (MPFProjectDir) (MPFProjectDir) (MPFProjectDir) (MPFProjectDir) (MPFProjectDir) (MPFProjectDir) (MPFProjectDir) (MPFProjectDir) (MPFProjectDir) (MPFProjectDir) (MPFProjectDir)*(DEV10) CSharp-ProjectBase.file

```
<!-- Provide a default value for $(ProjectBasePath) -->
  <PropertyGroup>
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>
  </PropertyGroup>
```

1. Создайте проект VSPackage.

2. Разгрузите проект VSPackage.

3. Оторите файл VSPackage .csproj, добавив `<Import>` следующий блок перед другими блоками:

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

2. Закройте и вновь откройте решение VSPackage.

3. Повторное открытие проекта VSPackage. Вы должны увидеть новый каталог под названием ProjectBase.

4. Добавьте следующую ссылку на проект VSPackage:

     Microsoft.Build.Tasks.4.0

5. Создайте проект.

## <a name="hierarchy-classes"></a>Классы иерархии
 В следующей таблице кратко излагаются классы в MPFProj, поддерживающие иерархии проектов. Для получения дополнительной [информации см.](../../extensibility/internals/hierarchies-and-selection.md)

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
 В следующей таблице перечислены классы в MPF, поддерживающие обработку документов. Для получения дополнительной информации [см.](../../extensibility/internals/opening-and-saving-project-items.md)

|Имя класса|
|----------------|
|`Microsoft.VisualStudio.Package.DocumentManager`|
|`Microsoft.VisualStudio.Package.FileDocumentManager`|

## <a name="configuration-and-output-classes"></a>Классы конфигурации и вывода
 В следующей таблице перечислены классы в MPF, которые позволяют типам проектов поддерживать несколько конфигураций, таких как отладка и выпуск, а также коллекции выходных проектов. Для получения дополнительной информации [см.](../../extensibility/internals/managing-configuration-options.md)

|Имя класса|
|----------------|
|`Microsoft.VisualStudio.Package.ConfigProvider`|
|`Microsoft.VisualStudio.Package.ProjectConfig`|
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|
|`Microsoft.VisualStudio.Package.OutputGroup`|
|`Microsoft.VisualStudio.Package.ProjectElement`|

## <a name="automation-support-classes"></a>Классы автоматизации поддержки
 В следующей таблице перечислены классы в MPF, которые поддерживают автоматизацию, чтобы пользователи вашего типа проекта могли писать надстройки.

|Имя класса|
|----------------|
|`Microsoft.VisualStudio.Package.Automation.OAProject`|
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|

## <a name="properties-classes"></a>Классы свойств
 В следующей таблице перечислены классы в MPF, которые позволяют типам проектов добавлять свойства, которые пользователи могут просматривать и изменять в браузере свойств.

|Имя класса|
|----------------|
|`Microsoft.VisualStudio.Package.LocalizableProperties`|
|`Microsoft.VisualStudio.Package.NodeProperties`|
|`Microsoft.VisualStudio.Package.FileNodeProperties`|
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|

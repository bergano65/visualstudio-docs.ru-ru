---
title: Поддержка проекта и свойства конфигурации | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, supporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f0428e2af6e273e961815ec2521ae26afb5e844d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322405"
---
# <a name="support-for-project-and-configuration-properties"></a>Поддержка свойств конфигурации и проекта
**Свойства** окно в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки (IDE) может отображать свойства проекта и конфигурации. Страницы свойств можно предоставить для типа проекта, таким образом, пользователь может задать свойства для вашего приложения.

 Выбрав узел проекта в **обозревателе решений** и выбрав **свойства** на **проекта** меню, можно открыть диалоговое окно, которое включает в себя проект и конфигурации свойства. В [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] и [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]и типы, производные от этих языков, это диалоговое окно с вкладками в виде страницы проекта [Общие, среда, диалоговое окно параметров](../../ide/reference/general-environment-options-dialog-box.md). Дополнительные сведения см. в разделе [не в сборке: Пошаговое руководство. Предоставление и свойств конфигурации проекта (C#)](https://msdn.microsoft.com/library/d850d63b-25e2-4505-9f3d-eb038d7c1d0e).

 Managed Package Framework для проектов (MPFProj) предоставляет вспомогательные классы для создания и управления новую систему проектов. Источник кода и компиляция инструкции доступны в [MPF для проектов — Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

## <a name="persistence-of-project-and-configuration-properties"></a>Длительное хранение и конфигурация свойств проекта
 Свойства проектов и конфигурации сохраняются в файле проекта, который имеет расширение имени файла, связанный с типом проекта, например, csproj, VBPROJ-файл и .myproj. Проекты на таких языках, обычно используется файл шаблона для создания файла проекта. Тем не менее фактически несколькими способами связать типы проектов и шаблоны. Дополнительные сведения см. в разделе [Описание каталога шаблона (. Файлы VSDir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).

 Свойства проектов и конфигурации создаются путем добавления элементов в файле шаблона. Затем эти свойства доступны для любого проекта, созданных с помощью типа проекта, использующего этот шаблон. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] проекты и MPFProj, используют [не в сборке: Общие сведения о MSBuild](/previous-versions/visualstudio/visual-studio-2008/ms171452(v=vs.90)) схемы для файлов шаблонов. Эти файлы имеют раздел PropertyGroup для каждой конфигурации. Свойства проектов обычно сохраняются в первом разделе PropertyGroup, имеет аргумент конфигурации присваивается пустая строка.

 В следующем коде показано начало базовый файл проекта MSBuild.

```
<Project MSBuildVersion="2.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <PropertyGroup>
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
    <Name>SomeProjectSix</Name>
    <SchemaVersion>2.0</SchemaVersion>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
    <Optimize>false</Optimize>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">
    <Optimize>true</Optimize>
```

 В данном файле проекта `<Name>` и `<SchemaVersion>` являются свойствами проекта и `<Optimize>` — это свойство конфигурации.

 Это ответственность за проект, чтобы сохранить свойства проекта и настройка файла проекта.

> [!NOTE]
> Проект можно оптимизировать сохраняемости, сохранение только значения свойств, которые отличаются от значения по умолчанию.

## <a name="support-for-project-and-configuration-properties"></a>Поддержка свойств конфигурации и проекта
 `Microsoft.VisualStudio.Package.SettingsPage` Класс реализует страницы свойств проекта и конфигурации. Реализация по умолчанию `SettingsPage` предоставляет открытые свойства для пользователя в сетке свойств. `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` Метод выбирает классы, производные от `SettingsPage` для сетки свойств проекта. `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` Метод выбирает классы, производные от `SettingsPage` для сетки свойств конфигурации. Ваш проект следует переопределить эти методы, чтобы выбрать соответствующее свойство.

 `SettingsPage` Класс и `Microsoft.VisualStudio.Package.ProjectNode` класс предлагают эти методы для сохранения свойств проекта и конфигурации:

- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` и `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` сохранения свойств проекта.

- `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` и `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` сохранения свойства конфигурации.

  > [!NOTE]
  > Реализации `Microsoft.VisualStudio.Package.SettingsPage` и `Microsoft.VisualStudio.Package.ProjectNode` классы используют `Microsoft.Build.BuildEngine` (MSBuild) методы для получения и задания свойств проекта и конфигурации из файла проекта.

  Класс производным от `SettingsPage` должен реализовывать `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` и `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` для сохранения свойства конфигурацию проекта или файла проекта.

## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute и путь в реестре
 Классы, производные от `SettingsPage` предназначены для совместно использоваться пакетов VSPackage. Чтобы облегчить VSPackage создать класс, производный от `SettingsPage`, добавьте `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` для класса, производного от `Microsoft.VisualStudio.Shell.Package`.

 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]

 Пакет VSPackage, к которой присоединен этот атрибут не имеет значения. При регистрации пакетов VSPackage с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], регистрируется идентификатор класса (CLSID) для любого объекта, который может быть создан таким образом, вызов <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> можно создать его.

 Путь в реестре, можно создать объект определяется путем объединения <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, word, CLSID и идентификатор guid типа объекта. Если `MyProjectPropertyPage` класс имеет guid {3c693da2-5bca-49b3-bd95-ffe0a39dd723} UserRegistryRoot является HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, затем путь реестра будет иметь HKEY_CURRENT_USER\Software\Microsoft\VisualStudio \8.0Exp\CLSID\\{3c693da2-5bca-49b3-bd95-ffe0a39dd723}.

## <a name="project-and-configuration-property-attributes-and-layout"></a>Проект и настройки атрибутов и свойств макета
 <xref:System.ComponentModel.CategoryAttribute>, <xref:System.ComponentModel.DisplayNameAttribute>, И <xref:System.ComponentModel.DescriptionAttribute> атрибуты определяют макета, добавления меток и описание свойств проекта и конфигурации на странице свойств. Эти атрибуты определения категории, отображаемое имя и описание параметра, соответственно.

> [!NOTE]
> Эквивалентное атрибуты, SRCategory, LocDisplayName и SRDescription, использование строковых ресурсов для локализации и определяются в [MPF для проектов — Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Рассмотрим следующий фрагмент кода:

 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]

 `MyConfigProp` Свойство конфигурации появится на странице свойств конфигурации, как **Мои свойство конфигурации** в категории **My Category**. Если параметр выбран, описание, **Мое описание**, отображается на панели «описание».

## <a name="see-also"></a>См. также
- [Добавление и удаление страниц свойств](../../extensibility/adding-and-removing-property-pages.md)
- [Проекты](../../extensibility/internals/projects.md)
- [Файлы описания каталога шаблона (VSDIR-файлы)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

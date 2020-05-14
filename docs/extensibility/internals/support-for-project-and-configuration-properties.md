---
title: Поддержка свойств проектов и конфигураций (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, supporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c21d552e26add3a5159febd666c1f60573697535
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704904"
---
# <a name="support-for-project-and-configuration-properties"></a>Поддержка свойств конфигурации и проекта
Окно **Свойств** в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среде разработки (IDE) может отображать свойства проекта и конфигурации. Вы можете предоставить страницу свойств для собственного типа проекта, чтобы пользователь мог установить свойства для приложения.

 Выбрав узла проекта в **Solution Explorer,** а затем нажав **на свойства** в меню **проекта,** можно открыть диалоговую коробку, которая включает свойства проекта и конфигурации. В [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]и , и типы проектов, полученных из этих языков, это диалоговое окно отображается как страница вкладок в [Общей среде, окружающей среде, параметры Dialog Box.](../../ide/reference/general-environment-options-dialog-box.md) Для получения дополнительной информации [см. Не в сборке: Пошаговая прогулка: Разоблачение проекта и свойства конфигурации (C)](https://msdn.microsoft.com/library/d850d63b-25e2-4505-9f3d-eb038d7c1d0e).

 Рамочная программа управляемого пакета для проектов (MPFProj) обеспечивает классы помощников для создания и управления новой системой проектов. Вы можете найти исходный код и инструкции по компиляции на [MPF для проектов - Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

## <a name="persistence-of-project-and-configuration-properties"></a>Сохранение свойств проекта и конфигурации
 Свойства проекта и конфигурации сохраняются в файле проекта, который имеет любое расширение имени файла, связанное с типом проекта, например, .csproj, .vbproj и .myproj. Языковые проекты обычно используют файл шаблона для создания файла проекта. Однако на самом деле существует несколько способов ассоциировать типы и шаблоны проектов. Для получения дополнительной информации см. [ Vsdir) Файлы](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).

 Свойства проекта и конфигурации создаются путем добавления элементов в файл шаблона. Эти свойства затем доступны для любого проекта, созданного с помощью типа проекта, использующего этот шаблон. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]проекты и MPFProj используют схему [Не в сборке:](/previous-versions/visualstudio/visual-studio-2008/ms171452(v=vs.90)) схема обзора MSBuild для файлов шаблонов. Эти файлы имеют раздел PropertyGroup для каждой конфигурации. Свойства проектов обычно сохраняются в первом разделе PropertyGroup, который имеет аргумент конфигурации, установленный на нулевую строку.

 Следующий код показывает начало базового файла проекта MSBuild.

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

 В этом файле проекта, `<Name>` и `<Optimize>` `<SchemaVersion>` свойства проекта, и является свойством конфигурации.

 Проект несет ответственность за сохранение свойств проекта и конфигурации файла проекта.

> [!NOTE]
> Проект может оптимизировать сохранение, сохраняя только значения свойств, которые отличаются от значений по умолчанию.

## <a name="support-for-project-and-configuration-properties"></a>Поддержка свойств конфигурации и проекта
 Класс `Microsoft.VisualStudio.Package.SettingsPage` реализует страницы свойств проекта и конфигурации. Реализация по `SettingsPage` умолчанию предлагает общедоступные свойства пользователю в общей сетке свойств. Метод `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` выбирает классы, `SettingsPage` полученные из сетки свойств проекта. Метод `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` выбирает классы, `SettingsPage` полученные из сетки свойств конфигурации. Тип проекта должен переопределить эти методы для выбора соответствующих страниц свойств.

 Класс `SettingsPage` и `Microsoft.VisualStudio.Package.ProjectNode` класс предлагают эти методы для сохранения свойств проекта и конфигурации:

- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty`и `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` сохраняют свойства проекта.

- `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty`и `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` сохраняют свойства конфигурации.

  > [!NOTE]
  > В реализациях `Microsoft.VisualStudio.Package.SettingsPage` `Microsoft.VisualStudio.Package.ProjectNode` и классах `Microsoft.Build.BuildEngine` используются методы (MSBuild) для получения и установки свойств проекта и конфигурации из файла проекта.

  Класс, из `SettingsPage` который `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` вы `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` получаете, должен реализовываться и сохранять свойства проекта или конфигурации файла проекта.

## <a name="provideobjectattribute-and-registry-path"></a>ОбеспечитьОбъектАтрибут и путь регистрации
 Классы, `SettingsPage` полученные из предназначены для совместного использования в VSPackages. Чтобы сделать возможным для VSPackage создать класс, полученный из, `SettingsPage`добавьте `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` к классу, полученному из. `Microsoft.VisualStudio.Shell.Package`

 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]

 VSPackage, к которому прилагается атрибут, не имеет значения. Когда VSPackage зарегистрирован [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]с, идентификатор класса (CLSID) любого объекта, <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> который может быть создан, регистрируется так, что вызов может создать его.

 Путь реестра объекта, который может быть создан, определяется путем объединения, <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>слова, CLSID и гида типа объекта. Если `MyProjectPropertyPage` класс имеет руководство no 3c693da2-5bca-49b3-bd95-ffe0a39dd723" и UserRegistryRoot HKEY_CURRENT_USER затем путь реестра будет HKEY_CURRENT_USER»Программное обеспечение»Microsoft-VisualStudio-8.0Exp-CLSID\\3c693da2-5bca-49b3-bd95-ffe0a39dd723».

## <a name="project-and-configuration-property-attributes-and-layout"></a>Атрибуты свойств проекта и конфигурации
 Атрибуты <xref:System.ComponentModel.CategoryAttribute>и <xref:System.ComponentModel.DescriptionAttribute> атрибуты определяют расположение, маркировку и описание свойств проекта и конфигурации на странице общего свойства. <xref:System.ComponentModel.DisplayNameAttribute> Эти атрибуты определяют категорию, имя дисплея и описание опциона, соответственно.

> [!NOTE]
> Эквивалентные атрибуты, SRCategory, LocDisplayName и SRDescription используют строковые ресурсы для локализации и определяются в [MPF для проектов - Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Рассмотрим следующий фрагмент кода:

 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]

 Свойство `MyConfigProp` конфигурации отображается на странице свойства конфигурации в качестве **свойства My Config** в категории **«Моя категория».** Если вариант выбран, описание, **Мое описание**, появляется в панели описания.

## <a name="see-also"></a>См. также
- [Добавление и удаление страниц свойств](../../extensibility/adding-and-removing-property-pages.md)
- [Проекты](../../extensibility/internals/projects.md)
- [Файлы описания каталога шаблона (VSDIR-файлы)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

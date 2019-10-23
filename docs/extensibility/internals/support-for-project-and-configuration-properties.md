---
title: Поддержка свойств проекта и конфигурации | Документация Майкрософт
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
ms.openlocfilehash: 8bf0581eee4fade779d89143f4633f1b87d3ce0f
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723159"
---
# <a name="support-for-project-and-configuration-properties"></a>Поддержка свойств конфигурации и проекта
В окне **Свойства** в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среде разработки (IDE) можно отобразить свойства проекта и конфигурации. Можно предоставить страницу свойств для собственного типа проекта, чтобы пользователь мог задать свойства приложения.

 Выбрав узел проекта в **Обозреватель решений** а затем выбрав пункт **свойства** в меню **проект** , можно открыть диалоговое окно, содержащее свойства проекта и конфигурации. В [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] и [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] и типах проектов, производных от этих языков, это диалоговое окно отображается как страница с вкладками в [диалоговом окне Общие, среда, параметры](../../ide/reference/general-environment-options-dialog-box.md). Дополнительные сведения см. в разделе [не в сборке. Пошаговое руководство. Предоставление свойств проектаC#и конфигурации ()](https://msdn.microsoft.com/library/d850d63b-25e2-4505-9f3d-eb038d7c1d0e).

 Платформа управляемых пакетов для проектов (Мпфпрож) предоставляет вспомогательные классы для создания новой системы проектов и управления ею. Исходный код и инструкции по компиляции можно найти по адресу [MPF for Projects-Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

## <a name="persistence-of-project-and-configuration-properties"></a>Сохраняемость свойств проекта и конфигурации
 Свойства проекта и конфигурации сохраняются в файле проекта, который имеет любое расширение имени файла, связанное с типом проекта, например. csproj,. vbproj и. мипрож. Проекты языка обычно используют файл шаблона для создания файла проекта. Однако существует несколько способов связывания типов проектов и шаблонов. Дополнительные сведения см. в разделе [шаблон описание каталога (. VSDir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).

 Свойства проекта и конфигурации создаются путем добавления элементов в файл шаблона. Затем эти свойства доступны для любого проекта, созданного с помощью типа проекта, который использует этот шаблон. для [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] проектов и Мпфпрож используется схема " [не в сборке". Обзор MSBuild](/previous-versions/visualstudio/visual-studio-2008/ms171452(v=vs.90)) для файлов шаблонов. Эти файлы имеют раздел PropertyGroup для каждой конфигурации. Свойства проектов обычно сохраняются в первом разделе PropertyGroup, для которого в качестве аргумента конфигурации задана пустая строка.

 В следующем коде показан запуск базового файла проекта MSBuild.

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

 В этом файле проекта `<Name>` и `<SchemaVersion>` являются свойствами проекта, а `<Optimize>` является свойством конфигурации.

 Проект отвечает за сохранение свойств проекта и конфигурации файла проекта.

> [!NOTE]
> Проект может оптимизировать сохранение путем сохранения только значений свойств, которые отличаются от значений по умолчанию.

## <a name="support-for-project-and-configuration-properties"></a>Поддержка свойств конфигурации и проекта
 Класс `Microsoft.VisualStudio.Package.SettingsPage` реализует страницы свойств проекта и конфигурации. Реализация `SettingsPage` по умолчанию предоставляет общие свойства пользователю в сетке универсальных свойств. Метод `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` выбирает классы, производные от `SettingsPage`, для сеток свойств проекта. Метод `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` выбирает классы, производные от `SettingsPage`, для сеток свойств конфигурации. Тип проекта должен переопределять эти методы, чтобы выбрать соответствующие страницы свойств.

 Класс `SettingsPage` и класс `Microsoft.VisualStudio.Package.ProjectNode` предлагают эти методы для сохранения свойств проекта и конфигурации:

- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` и `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` сохранить свойства проекта.

- `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` и `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` сохранять свойства конфигурации.

  > [!NOTE]
  > Реализации классов `Microsoft.VisualStudio.Package.SettingsPage` и `Microsoft.VisualStudio.Package.ProjectNode` используют методы `Microsoft.Build.BuildEngine` (MSBuild) для получения и задания свойств проекта и конфигурации из файла проекта.

  Класс, производный от `SettingsPage`, должен реализовывать `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` и `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` для сохранения свойств проекта или конфигурации файла проекта.

## <a name="provideobjectattribute-and-registry-path"></a>Провидеобжектаттрибуте и путь реестра
 Классы, производные от `SettingsPage`, предназначены для совместного использования в пакетах VSPackage. Чтобы пакет VSPackage можно было создать класс, производный от `SettingsPage`, добавьте `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` в класс, производный от `Microsoft.VisualStudio.Shell.Package`.

 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]

 Пакет VSPackage, к которому присоединен атрибут, не важен. При регистрации VSPackage с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] идентификатор класса (CLSID) любого объекта, который может быть создан, регистрируется таким образом, что вызов <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> может создать его.

 Путь реестра объекта, который может быть создан, определяется сочетанием <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, слова, CLSID и идентификатора GUID типа объекта. Если `MyProjectPropertyPage` класс имеет идентификатор GUID {3c693da2-5bca-49b3-bd95-ffe0a39dd723}, а Усеррегистрирут — HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, то путь реестра будет HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\ 8.0 exp \ CLSID \\ {3c693da2-5bca-49b3-bd95-ffe0a39dd723}.

## <a name="project-and-configuration-property-attributes-and-layout"></a>Атрибуты и макет свойств проекта и конфигурации
 Атрибуты <xref:System.ComponentModel.CategoryAttribute>, <xref:System.ComponentModel.DisplayNameAttribute> и <xref:System.ComponentModel.DescriptionAttribute> определяют макет, метки и описание свойств проекта и конфигурации на странице универсальных свойств. Эти атрибуты определяют категорию, отображаемое имя и описание параметра соответственно.

> [!NOTE]
> Эквивалентные атрибуты, Сркатегори, Локдисплайнаме и Срдескриптион, используют строковые ресурсы для локализации и определяются в [MPF для проектов — Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Рассмотрим следующий фрагмент кода:

 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]

 Свойство конфигурации `MyConfigProp` отображается на странице свойств Конфигурация как **свойство config** в категории " **Моя Категория**". Если выбран этот параметр, описание « **мое описание**» отображается на панели «Описание».

## <a name="see-also"></a>См. также
- [Добавление и удаление страниц свойств](../../extensibility/adding-and-removing-property-pages.md)
- [Проекты](../../extensibility/internals/projects.md)
- [Файлы описания каталога шаблона (VSDIR-файлы)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

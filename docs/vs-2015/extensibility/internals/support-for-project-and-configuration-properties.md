---
title: Поддержка свойств проекта и конфигурации | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, suppporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b03bc04b1d5b87219110aa65bee53c4a4a8f77e2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "74301075"
---
# <a name="support-for-project-and-configuration-properties"></a>Поддержка свойств конфигурации и проекта
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Окно **Свойства** в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] интегрированной среде разработки (IDE) может отображать свойства проекта и конфигурации. Можно предоставить страницу свойств для собственного типа проекта, чтобы пользователь мог задать свойства приложения.  
  
 Выбрав узел проекта в **Обозреватель решений** а затем выбрав пункт **свойства** в меню **проект** , можно открыть диалоговое окно, содержащее свойства проекта и конфигурации. В [!INCLUDE[csprcs](../../includes/csprcs-md.md)] и [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] типы проектов, производные от этих языков, это диалоговое окно отображается как страница с вкладками в [диалоговом окне Общие, среда, параметры](../../ide/reference/general-environment-options-dialog-box.md). Дополнительные сведения см. в разделе [не в сборке. Пошаговое руководство. Предоставление свойств проекта и конфигурации (C#)](https://msdn.microsoft.com/d850d63b-25e2-4505-9f3d-eb038d7c1d0e).  
  
 Платформа управляемых пакетов для проектов (Мпфпрож) предоставляет вспомогательные классы для создания новой системы проектов и управления ею. Исходный код и инструкции по компиляции можно найти по адресу [MPF for Projects-Visual Studio 2013](https://archive.codeplex.com/?p=mpfproj12).  
  
## <a name="persistence-of-project-and-configuration-properties"></a>Сохраняемость свойств проекта и конфигурации  
 Свойства проекта и конфигурации сохраняются в файле проекта, который имеет расширение имени файла, связанное с типом проекта, например. csproj,. vbproj и. мипрож. Проекты языка обычно используют файл шаблона для создания файла проекта. Однако существует несколько способов связывания типов проектов и шаблонов. Дополнительные сведения см. в разделе [NIB: шаблоны Visual Studio](https://msdn.microsoft.com/141fccaa-d68f-4155-822b-27f35dd94041) и [Описание каталога шаблонов (. VSDir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
 Свойства проекта и конфигурации создаются путем добавления элементов в файл шаблона. Затем эти свойства доступны для любого проекта, созданного с помощью типа проекта, который использует этот шаблон. [!INCLUDE[csprcs](../../includes/csprcs-md.md)] в проектах и Мпфпрож используется схема " [не в сборке": обзор MSBuild](https://msdn.microsoft.com/b588fd73-a45b-4706-908f-cc131bccfbde) для файлов шаблонов. Эти файлы имеют раздел PropertyGroup для каждой конфигурации. Свойства проектов обычно сохраняются в первом разделе PropertyGroup, для которого в качестве аргумента конфигурации задана пустая строка.  
  
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
  
 В этом файле проекта `<Name>` и `<SchemaVersion>` являются свойствами проекта, а `<Optimize>` — свойством конфигурации.  
  
 Проект отвечает за сохранение свойств проекта и конфигурации файла проекта.  
  
> [!NOTE]
> Проект может оптимизировать сохранение путем сохранения только значений свойств, которые отличаются от значений по умолчанию.  
  
## <a name="support-for-project-and-configuration-properties"></a>Поддержка свойств конфигурации и проекта  
 `Microsoft.VisualStudio.Package.SettingsPage`Класс реализует страницы свойств проекта и конфигурации. Реализация по умолчанию `SettingsPage` предоставляет общие свойства пользователю в сетке универсальных свойств. `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids`Метод выбирает классы, производные от `SettingsPage` , для сеток свойств проекта. `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids`Метод выбирает классы, производные от `SettingsPage` , для сеток свойств конфигурации. Тип проекта должен переопределять эти методы, чтобы выбрать соответствующие страницы свойств.  
  
 `SettingsPage`Класс и `Microsoft.VisualStudio.Package.ProjectNode` класс предлагают эти методы для сохранения свойств проекта и конфигурации:  
  
- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` и `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` сохранить свойства проекта.  
  
- `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` и `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` сохраняют свойства конфигурации.  
  
  > [!NOTE]
  > Реализации `Microsoft.VisualStudio.Package.SettingsPage` `Microsoft.VisualStudio.Package.ProjectNode` классов и используют `Microsoft.Build.BuildEngine` методы (MSBuild) для получения и задания свойств проекта и конфигурации из файла проекта.  
  
  Класс, производный от, `SettingsPage` должен реализовывать `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` и `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` сохранять свойства проекта или конфигурации файла проекта.  
  
## <a name="provideobjectattribute-and-registry-path"></a>Провидеобжектаттрибуте и путь реестра  
 Классы, производные от `SettingsPage` , предназначены для совместного использования в пакетах VSPackage. Чтобы пакет VSPackage может создать класс, производный от `SettingsPage` , добавьте `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` в класс, производный от `Microsoft.VisualStudio.Shell.Package` .  
  
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/cs/vssdksupportprojectconfigurationpropertiespackage.cs#1)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/vb/vssdksupportprojectconfigurationpropertiespackage.vb#1)]  
  
 Пакет VSPackage, к которому присоединен атрибут, не важен. При регистрации VSPackage с помощью [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] регистрируется идентификатор класса (CLSID) любого объекта, который может быть создан, чтобы <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> можно было создать его.  
  
 Путь реестра объекта, который можно создать, определяется путем объединения <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A> , слова, CLSID и идентификатора GUID типа объекта. Если `MyProjectPropertyPage` класс имеет идентификатор GUID {3c693da2-5bca-49b3-bd95-ffe0a39dd723}, а усеррегистрирут — HKEY_CURRENT_USER \software\microsoft\visualstudio\8.0exp, то путь реестра будет HKEY_CURRENT_USER \software\microsoft\visualstudio\8.0exp\clsid \\ {3c693da2-5bca-49b3-bd95-ffe0a39dd723}.  
  
## <a name="project-and-configuration-property-attributes-and-layout"></a>Атрибуты и макет свойств проекта и конфигурации  
 <xref:System.ComponentModel.CategoryAttribute>Атрибуты, <xref:System.ComponentModel.DisplayNameAttribute> и <xref:System.ComponentModel.DescriptionAttribute> определяют макет, метки и описание свойств проекта и конфигурации на странице универсальных свойств. Эти атрибуты определяют категорию, отображаемое имя и описание параметра соответственно.  
  
> [!NOTE]
> Эквивалентные атрибуты, Сркатегори, Локдисплайнаме и Срдескриптион, используют строковые ресурсы для локализации и определяются в [MPF для проектов — Visual Studio 2013](https://archive.codeplex.com/?p=mpfproj12).  
  
 Рассмотрим следующий фрагмент кода:  
  
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../snippets/csharp/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/cs/myprojectpropertypage.cs#2)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../snippets/visualbasic/VS_Snippets_VSSDK/vssdksupportprojectconfigurationproperties/vb/myprojectpropertypage.vb#2)]  
  
 `MyConfigProp`Свойство конфигурации отображается на странице свойств Конфигурация как **свойство config** в категории " **Моя Категория**". Если выбран этот параметр, описание « **мое описание**» отображается на панели «Описание».  
  
## <a name="see-also"></a>См. также:  
 [Не в сборке. Пошаговое руководство. Предоставление свойств проекта и конфигурации (C#)](https://msdn.microsoft.com/d850d63b-25e2-4505-9f3d-eb038d7c1d0e)   
 [Добавление и удаление страниц свойств](../../extensibility/adding-and-removing-property-pages.md)   
 [Состояние VSPackage](../../misc/vspackage-state.md)   
 [Макропроекты](../../extensibility/internals/projects.md)   
 [NIB: шаблоны Visual Studio](https://msdn.microsoft.com/141fccaa-d68f-4155-822b-27f35dd94041)   
 [Файлы описания каталога шаблона (VSDIR-файлы)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

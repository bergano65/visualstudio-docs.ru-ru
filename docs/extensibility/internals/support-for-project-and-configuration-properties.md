---
title: Поддержка проектов и свойства конфигурации | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, suppporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 823bfa0453d3e33fea2daa51779b1fe4800a1a86
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="support-for-project-and-configuration-properties"></a>Поддержка и свойств конфигурации проекта
**Свойства** окна в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки (IDE) может отображать свойства проекта и конфигурации. Чтобы обеспечить страницу свойств для типа проекта, чтобы пользователь может задать свойства для вашего приложения.  
  
 Выбрав узел проекта в **обозревателе решений** и выбрав **свойства** на **проекта** меню, можно открыть диалоговое окно, проект и конфигурации свойства. В [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] и [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]и типы, производные от этих языков, это диалоговое окно с вкладками в виде страницы проекта [Общие, среда, диалоговое окно «Параметры»](../../ide/reference/general-environment-options-dialog-box.md). Дополнительные сведения см. в разделе [не в сборке: пошаговое руководство: предоставление свойства проектов и конфигурации (C#)](http://msdn.microsoft.com/en-us/d850d63b-25e2-4505-9f3d-eb038d7c1d0e).  
  
 Managed Package Framework для проектов (MPFProj) предоставляет вспомогательные классы для создания и управления новую систему проектов. Найти источник кода и компиляция инструкции в [MPF для проектов - Visual Studio 2013](http://mpfproj12.codeplex.com/).  
  
## <a name="persistence-of-project-and-configuration-properties"></a>Сохранение и настройка свойств проекта  
 Свойства проектов и конфигурации сохраняются в файле проекта, который имеет расширение имени файла, связанного с типом проекта, например, .csproj, .vbproj и .myproj. Обычно проекты языка использовать файл шаблона для создания файла проекта. Однако фактически несколькими способами для связи типа и шаблонов проекта. Дополнительные сведения см. в разделе [описание шаблона каталога (. Файлы VSDir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
 Свойства проектов и конфигурации создаются путем добавления элементов в файле шаблона. Затем эти свойства доступны для любой проект, созданный с помощью типа проекта, использующего этот шаблон. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] проекты и MPFProj, используют [не в сборке: Обзор MSBuild](http://msdn.microsoft.com/en-us/b588fd73-a45b-4706-908f-cc131bccfbde) схема для файлов шаблонов. Эти файлы имеют раздел PropertyGroup для каждой конфигурации. Свойства проектов обычно сохраняются в первом разделе PropertyGroup, имеет аргумент конфигурации пустой строкой.  
  
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
  
 В этом файле проекта `<Name>` и `<SchemaVersion>` являются свойства проекта и `<Optimize>` — это свойство конфигурации.  
  
 Он отвечает проекта для сохранения свойства проекта и конфигурации в файл проекта.  
  
> [!NOTE]
>  Проект можно оптимизировать сохраняемости, сохранение только значения свойств, отличные от значения по умолчанию.  
  
## <a name="support-for-project-and-configuration-properties"></a>Поддержка и свойств конфигурации проекта  
 `Microsoft.VisualStudio.Package.SettingsPage` Класс реализует страницы свойств проекта и конфигурации. Реализация по умолчанию `SettingsPage` предлагает открытые свойства для пользователя в сетке свойств. `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` Классы, производные от выбирает метод `SettingsPage` для сетки свойств проекта. `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` Классы, производные от выбирает метод `SettingsPage` для сетки свойств конфигурации. Типа проекта следует переопределить эти методы для выделения страниц соответствующее свойство.  
  
 `SettingsPage` Класса и `Microsoft.VisualStudio.Package.ProjectNode` класса предоставляют эти методы для сохранения свойства проекта и конфигурации:  
  
-   `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` и `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` сохранять сведения о свойствах проекта.  
  
-   `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` и `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` сохранения свойств конфигурации.  
  
    > [!NOTE]
    >  Реализации `Microsoft.VisualStudio.Package.SettingsPage` и `Microsoft.VisualStudio.Package.ProjectNode` классы используют `Microsoft.Build.BuildEngine` методы get и set свойства проекта и конфигурации из файла проекта (MSBuild).  
  
 Класс производным от `SettingsPage` необходимо реализовать `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` и `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` для сохранения свойства конфигурацию проекта или файла проекта.  
  
## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute и реестра путь  
 Классы, производные от `SettingsPage` предназначены для совместного использования в пакеты VSPackage. Чтобы сделать возможным для VSPackage создать класс, производный от `SettingsPage`, добавьте `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` для класса, производного от `Microsoft.VisualStudio.Shell.Package`.  
  
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]  
  
 Пакет VSPackage, к которой присоединен этот атрибут не имеет значения. При регистрации пакетов VSPackage с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], зарегистрированные идентификатор класса (CLSID) для любого объекта, который может быть создан, чтобы вызов <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> можно создать его.  
  
 Путь реестра для объекта, который может быть создан определяется путем объединения <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, слово, идентификатор CLSID и идентификатор guid типа объекта. Если `MyProjectPropertyPage` класс имеет guid {3c693da2-5bca-49b3-bd95-ffe0a39dd723} а UserRegistryRoot HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, то путь реестра будет иметь HKEY_CURRENT_USER\Software\Microsoft\VisualStudio \8.0Exp\CLSID\\{3c693da2-5bca-49b3-bd95-ffe0a39dd723}.  
  
## <a name="project-and-configuration-property-attributes-and-layout"></a>Проект и настройки атрибутов и свойств макета  
 <xref:System.ComponentModel.CategoryAttribute>, <xref:System.ComponentModel.DisplayNameAttribute>, И <xref:System.ComponentModel.DescriptionAttribute> атрибуты определяют разметки, пометку и описание свойств проекта и конфигурации на странице свойств. Эти атрибуты определения категории, отображаемое имя и описание параметра, соответственно.  
  
> [!NOTE]
>  Эквивалент атрибуты, SRCategory, LocDisplayName и SRDescription, использование строковых ресурсов для локализации и определены в [MPF для проектов - Visual Studio 2013](http://mpfproj12.codeplex.com/).  
  
 Рассмотрим следующий фрагмент кода:  
  
 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]  
  
 `MyConfigProp` Свойство конфигурации отображается на странице свойств конфигурации, как **Мои свойство конфигурации** в категории, **Мои категории**. Если параметр выбран, описание, **Мое описание**, отображается на панели «описание».  
  
## <a name="see-also"></a>См. также  
 [Добавление и удаление страниц свойств](../../extensibility/adding-and-removing-property-pages.md)   
 [Проекты](../../extensibility/internals/projects.md)   
 [Файлы описания каталога шаблона (VSDIR-файлы)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)

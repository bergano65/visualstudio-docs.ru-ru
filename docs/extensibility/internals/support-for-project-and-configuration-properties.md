---
title: "Поддержка и свойств конфигурации проекта | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Свойства проекта, поддерживая с Visual Studio SDK"
  - "Свойства конфигурации, suppporting с Visual Studio SDK"
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
caps.latest.revision: 25
caps.handback.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
---
# Поддержка и свойств конфигурации проекта
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

**Свойства** окна в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] интегрированной среды разработки \(IDE\) может отображать свойства проектов и конфигурации. Можно предоставить страницу свойств для типа проекта, чтобы пользователь может задать свойства для вашего приложения.  
  
 Выбрав узел проекта в **обозревателе решений** и выбрав **Свойства** на **проекта** меню, можно открыть диалоговое окно содержит свойства проектов и конфигурации. В [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] и [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], и типы, производные от этих языков, оно появляется в виде вкладки окна проекта [Страница "Общие", папка "Среда", диалоговое окно "Параметры"](../../ide/reference/general-environment-options-dialog-box.md). Дополнительные сведения см. в разделе [не в построении: пошаговое руководство: предоставление проектов и свойствами конфигурации \(C\#\)](http://msdn.microsoft.com/ru-ru/d850d63b-25e2-4505-9f3d-eb038d7c1d0e).  
  
 Платформа управляемых пакетов для проектов \(MPFProj\) предоставляет вспомогательные классы для создания и управления новой системы проектов. Найти источник кода и компиляция инструкции в [MPF проектов — Visual Studio 2013](http://mpfproj12.codeplex.com/).  
  
## Сохранение и свойств конфигурации проекта  
 Свойства проектов и конфигурации сохраняются в файле проекта, который имеет расширение имени файла, связанного с типом проекта, например, с расширением .csproj, .vbproj и .myproj. Проекты языка обычно используют файл шаблона для создания файла проекта. Однако на самом деле несколькими способами для связывания шаблонов и типов проекта. Дополнительные сведения см. в разделе [NIB: шаблоны Visual Studio](http://msdn.microsoft.com/ru-ru/141fccaa-d68f-4155-822b-27f35dd94041) и [Описание шаблона каталога \(. Файлы VSDir\)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
 Свойства проектов и конфигурации создаются путем добавления элементов в файле шаблона. Затем эти свойства доступны для любого проекта, созданных с помощью типа проекта, использующего этот шаблон.[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] проекты и MPFProj, используют [не в построении: Обзор MSBuild](http://msdn.microsoft.com/ru-ru/b588fd73-a45b-4706-908f-cc131bccfbde) схема для файлов шаблонов. Эти файлы имеют раздел PropertyGroup для каждой конфигурации. Свойства проектов обычно сохраняются в первом разделе PropertyGroup, имеет аргумент конфигурации пустую строку.  
  
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
  
 Это ответственность за сохранение файла проекта свойства проекта и конфигурации проекта.  
  
> [!NOTE]
>  Проект можно оптимизировать сохраняемости, сохранение только значения свойств, которые отличаются от значений по умолчанию.  
  
## Поддержка и свойств конфигурации проекта  
 `Microsoft.VisualStudio.Package.SettingsPage` Класс реализует на страницах свойств проекта и конфигурации. Реализация по умолчанию `SettingsPage` предлагает открытых свойств пользователя в сетке свойств.`Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` Метод выбирает классы, производные от `SettingsPage` для сетки свойств проекта.`Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` Метод выбирает классы, производные от `SettingsPage` для сетки свойств конфигурации. Проект типа должен переопределить эти методы для выбора соответствующих свойств.  
  
 `SettingsPage` Класса и `Microsoft.VisualStudio.Package.ProjectNode` класс предлагают следующие методы для сохранения свойств проекта и конфигурации:  
  
-   `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` и `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` сохранения свойств проекта.  
  
-   `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` и `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` сохранения свойства конфигурации.  
  
    > [!NOTE]
    >  Реализации `Microsoft.VisualStudio.Package.SettingsPage` и `Microsoft.VisualStudio.Package.ProjectNode` классы используют `Microsoft.Build.BuildEngine` методы get и set свойства проектов и конфигурации из файла проекта \(MSBuild\).  
  
 Класс производным от `SettingsPage` необходимо реализовать `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` и `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` для сохранения свойств конфигурацию проекта или файла проекта.  
  
## ProvideObjectAttribute и путь реестра  
 Классы, производные от `SettingsPage` предназначены для совместного использования через пакеты VSPackage. Чтобы сделать возможным для VSPackage создать класс, производный от `SettingsPage`, добавьте `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` в класс, производный от `Microsoft.VisualStudio.Shell.Package`.  
  
 [!code-cs[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]  
  
 VSPackage, к которой присоединен этот атрибут не имеет значения. При регистрации VSPackage с [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], регистрируется идентификатор класса \(CLSID\) для любого объекта, который может быть создан, чтобы вызов <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> можно создать его.  
  
 Пути в реестре, можно создать объект определяется путем объединения <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, word, CLSID и идентификатор guid типа объекта. Если `MyProjectPropertyPage` класс имеет идентификатор guid {3c693da2\-5bca\-49b3\-bd95\-ffe0a39dd723} и UserRegistryRoot — HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0Exp, а затем путь реестра будет HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0Exp\\CLSID\\{3c693da2\-5bca\-49b3\-bd95\-ffe0a39dd723}.  
  
## Проект и настройки атрибутов и свойств макета  
 <xref:System.ComponentModel.CategoryAttribute>, <xref:System.ComponentModel.DisplayNameAttribute>, И <xref:System.ComponentModel.DescriptionAttribute> атрибуты определяют макет, метки и описания свойств проекта и конфигурации на странице свойств. Эти атрибуты определить категорию, отображаемое имя и описание параметра, соответственно.  
  
> [!NOTE]
>  Эквивалент атрибуты, SRCategory, LocDisplayName и SRDescription, использование строковых ресурсов для локализации и определены в [MPF проектов — Visual Studio 2013](http://mpfproj12.codeplex.com/).  
  
 Рассмотрим следующий фрагмент кода:  
  
 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-cs[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]  
  
 `MyConfigProp` Свойство конфигурации отображается на странице свойств конфигурации, как **Мои свойство конфигурации** в категории **Мои категории**. Если данный параметр выбран, описание, **Мое описание**, отображается на панели «описание».  
  
## См. также  
 [Не в построении: пошаговое руководство: предоставление проектов и свойствами конфигурации \(C\#\)](http://msdn.microsoft.com/ru-ru/d850d63b-25e2-4505-9f3d-eb038d7c1d0e)   
 [Добавление и удаление страницы свойств](../../extensibility/adding-and-removing-property-pages.md)   
 [Состояние VSPackage](/visual-cpp/misc/vspackage-state)   
 [Проекты](../../extensibility/internals/projects.md)   
 [NIB: шаблоны Visual Studio](http://msdn.microsoft.com/ru-ru/141fccaa-d68f-4155-822b-27f35dd94041)   
 [Описание шаблона каталога \(. Файлы VSDir\)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
---
title: "Задача UpdateManifestForBrowserApplication | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "добавление элемента <hostInBrowser /> в манифест приложения [WPF MSBuild]"
  - "построение проектов XBAP [WPF MSBuild]"
  - "UpdateManifestForBrowserApplication - задача [WPF MSBuild]"
  - "UpdateManifestForBrowserApplication - задача [WPF MSBuild], параметры"
ms.assetid: 653339f7-654b-4d64-a26a-5c9f27036895
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Задача UpdateManifestForBrowserApplication
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Задача <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> выполняется для добавления элемента **\<hostInBrowser \/\>** в манифест приложения \(*имя\_проекта*.exe.manifest\) при сборке проекта [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)].  
  
## Параметры задачи  
  
|Параметр|Описание|  
|--------------|--------------|  
|`ApplicationManifest`|Требуется параметр **ITaskItem \[\]**.<br /><br /> Задает путь и имя файла манифеста приложения, в который необходимо добавить элемент `<hostInBrowser />`.|  
|`HostInBrowser`|Требуется параметр **Boolean**.<br /><br /> Указывает, следует ли изменить манифест приложения для включения элемента **\<hostInBrowser \/\>**.  Если задано значение **true**, новый элемент `<`**hostInBrowser \/\>** включается в элемент **\<entryPoint \/\>**.  Обратите внимание, что включение элемента является накопительным: если элемент **\<hostInBrowser \/\>** уже существует, он не удаляется и не перезаписывается.  Вместо этого создается дополнительный элемент **\<hostInBrowser \/\>**.  Если указано значение **false**, манифест приложения не изменяется.|  
  
## Заметки  
 [!INCLUDE[TLA2#tla_xbap#plural](../msbuild/includes/tla2sharptla_xbapsharpplural_md.md)] запускаются с помощью развертывания [!INCLUDE[TLA#tla_clickonce](../msbuild/includes/tlasharptla_clickonce_md.md)] и, следовательно, должны публиковаться с поддерживающими манифестами развертывания и приложения.  [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] использует задачу [GenerateApplicationManifest](http://msdn2.microsoft.com/library/6wc2ccdc.aspx) для создания манифеста приложения.  
  
 Затем, чтобы настроить приложение для размещения из браузера, необходимо добавить в манифест приложения дополнительный элемент **\<hostInBrowser \/\>**, как показано в следующем примере.  
  
```  
<!--MyXBAPApplication.exe.manifest-->  
<?xml version="1.0" encoding="utf-8"?>  
<asmv1:assembly ... >  
    <asmv1:assemblyIdentity ... />  
    <application />  
    <entryPoint>  
      ...  
      <hostInBrowser xmlns="urn:schemas-microsoft-com:asm.v3" />  
    </entryPoint>  
  ...  
/>  
```  
  
 Задача <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> запускается, когда выполняется сборка проекта [!INCLUDE[TLA2#tla_xbap](../msbuild/includes/tla2sharptla_xbap_md.md)] для добавления элемента `<hostInBrowser />`.  
  
## Пример  
 В следующем примере показано, как убедиться, что элемент `<hostInBrowser />` включен в файл манифеста приложения.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication"  
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="UpdateManifestForBrowserApplicationTask">  
    <UpdateManifestForBrowserApplication  
      ApplicationManifest="MyXBAPApplication.exe.manifest"  
      HostInBrowser="true" />  
  </Target>  
</Project>  
```  
  
## См. также  
 [Справочные сведения о WPF для MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Справочные сведения о задачах](../msbuild/wpf-msbuild-task-reference.md)   
 [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Построение приложения WPF](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)   
 [Общие сведения о приложениях браузера WPF XAML](../Topic/WPF%20XAML%20Browser%20Applications%20Overview.md)
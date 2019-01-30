---
title: Задача UpdateManifestForBrowserApplication | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UpdateManifestForBrowserApplication task [WPF MSBuild]
- adding the <hostInBrowser /> element to the application manifest [WPF MSBuild]
- building XBAP projects [WPF MSBuild]
- UpdateManifestForBrowserApplication task [WPF MSBuild], parameters
ms.assetid: 653339f7-654b-4d64-a26a-5c9f27036895
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d9d3cb96912e411109514e099fbd6b4780fd00c4
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54936883"
---
# <a name="updatemanifestforbrowserapplication-task"></a>Задача UpdateManifestForBrowserApplication
Задача <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> выполняется для добавления элемента **\<hostInBrowser />** в манифест приложения (*\<имя_проекта>.exe.manifest*) при сборке проекта [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)].  
  
## <a name="task-parameters"></a>Параметры задачи  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`ApplicationManifest`|Обязательный параметр **ITaskItem[]**.<br /><br /> Задает путь и имя файла манифеста приложения, в который необходимо добавить элемент `<hostInBrowser />`.|  
|`HostInBrowser`|Обязательный параметр **Boolean**.<br /><br /> Указывает, следует ли изменить манифест приложения для включения элемента **\<hostInBrowser />**. Если задано значение **true**, новый элемент **\<hostInBrowser />** включается в элемент **\<entryPoint />**. Включение элемента является накопительным: если элемент **\<hostInBrowser />** уже существует, он не удаляется и не перезаписывается. Вместо этого создается дополнительный элемент **\<hostInBrowser />**. Если задано значение **false**, манифест приложения не изменяется.|  
  
## <a name="remarks"></a>Примечания  
 Приложения [!INCLUDE[TLA2#tla_xbap#plural](../msbuild/includes/tla2sharptla_xbapsharpplural_md.md)] запускаются с помощью развертывания [!INCLUDE[TLA#tla_clickonce](../msbuild/includes/tlasharptla_clickonce_md.md)] и, следовательно, должны публиковаться с соответствующими манифестами развертывания и приложения. [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] создает манифест приложения с помощью задачи [GenerateApplicationManifest](generateapplicationmanifest-task.md).  
  
 Затем, чтобы настроить приложение для размещения из браузера, необходимо добавить в манифест приложения дополнительный элемент **\<hostInBrowser />**, как показано в примере ниже.  
  
```xml  
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
  
## <a name="example"></a>Пример  
 В следующем примере показано, как убедиться, что элемент `<hostInBrowser />` включен в файл манифеста приложения.  
  
```xml  
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
  
## <a name="see-also"></a>См. также  
 [Справочные сведения о WPF для MSBuild](../msbuild/wpf-msbuild-reference.md)   
 [Справочные сведения о задачах](../msbuild/wpf-msbuild-task-reference.md)   
 [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)   
 [Создание приложения WPF](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)   
 [Общие сведения о приложениях браузера WPF XAML](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)
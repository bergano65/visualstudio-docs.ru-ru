---
title: Задача UpdateManifestForBrowserApplication | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6dffa98a8abbf74bd6eee8761d91f09a7c022666
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68740222"
---
# <a name="updatemanifestforbrowserapplication-task"></a>Задача UpdateManifestForBrowserApplication
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

<xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication>Задача выполняется для добавления **\<hostInBrowser />** элемента в манифест приложения (*имяПроекта*. exe. manifest) при [!INCLUDE[TLA#tla_xbap](../includes/tlasharptla-xbap-md.md)] построении проекта.  
  
## <a name="task-parameters"></a>Параметры задачи  
  
|Параметр|Описание|  
|---------------|-----------------|  
|`ApplicationManifest`|Обязательный параметр **ITaskItem[]** .<br /><br /> Задает путь и имя файла манифеста приложения, в который необходимо добавить элемент `<hostInBrowser />`.|  
|`HostInBrowser`|Обязательный параметр **Boolean**.<br /><br /> Указывает, следует ли изменить манифест приложения, включив в него **\<hostInBrowser />** элемент. Если **значение — true**, `<` в элемент включается новый элемент **HostInBrowser/>** **\<entryPoint />** . Обратите внимание, что включение элемента является накопительным: Если **\<hostInBrowser />** элемент уже существует, он не удаляется и не перезаписывается. Вместо этого создается дополнительный **\<hostInBrowser />** элемент. Если указано значение **false**, манифест приложения не изменяется.|  
  
## <a name="remarks"></a>Примечания  
 [!INCLUDE[TLA2#tla_xbap#plural](../includes/tla2sharptla-xbapsharpplural-md.md)] запускаются с помощью развертывания [!INCLUDE[TLA#tla_clickonce](../includes/tlasharptla-clickonce-md.md)] и, следовательно, должны публиковаться с поддерживающими манифестами развертывания и приложения. [!INCLUDE[TLA#tla_msbuild](../includes/tlasharptla-msbuild-md.md)] создает манифест приложения с помощью задачи [GenerateApplicationManifest](/dotnet/api/microsoft.build.tasks.generateapplicationmanifest).  
  
 Затем, чтобы настроить приложение для размещения из браузера, **\<hostInBrowser />** необходимо добавить в манифест приложения дополнительный элемент, как показано в следующем примере:  
  
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
  
 Задача <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> запускается, когда выполняется сборка проекта [!INCLUDE[TLA2#tla_xbap](../includes/tla2sharptla-xbap-md.md)] для добавления элемента `<hostInBrowser />`.  
  
## <a name="example"></a>Пример  
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
  
## <a name="see-also"></a>См. также:  
 [Справочник по MSBuild для WPF](../msbuild/wpf-msbuild-reference.md)   
 [Справочник по задачам](../msbuild/wpf-msbuild-task-reference.md)   
 [Справочник по MSBuild](../msbuild/msbuild-reference.md)   
 [Справочник по задачам](../msbuild/msbuild-task-reference.md)   
 [Создание приложения WPF (WPF)](https://msdn.microsoft.com/library/a58696fd-bdad-4b55-9759-136dfdf8b91c)   
 [Общие сведения о приложениях браузера WPF XAML](https://msdn.microsoft.com/library/3a7a86a8-75d5-4898-96b9-73da151e5e16)

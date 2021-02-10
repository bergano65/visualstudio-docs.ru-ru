---
title: Задача UpdateManifestForBrowserApplication | Документация Майкрософт
description: Узнайте, как с помощью задачи UpdateManifestForBrowserApplication в MSBuild добавить элемент hostInBrowser в манифест приложения.
ms.custom: SEO-VS-2020
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9e71e11988d4dd853b0f97c745b6d720a45adcdc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961551"
---
# <a name="updatemanifestforbrowserapplication-task"></a>Задача UpdateManifestForBrowserApplication

Задача <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> выполняется для добавления элемента **\<hostInBrowser />** в манифест приложения ( *\<projectname>.exe.manifest*) при сборке проекта Приложение обозревателя XAML (XBAP).

## <a name="task-parameters"></a>Параметры задачи

|Параметр|Описание|
|---------------|-----------------|
|`ApplicationManifest`|Обязательный параметр **ITaskItem[]** .<br /><br /> Задает путь и имя файла манифеста приложения, в который необходимо добавить элемент `<hostInBrowser />`.|
|`HostInBrowser`|Обязательный параметр **Boolean**.<br /><br /> Указывает, следует ли изменить манифест приложения для включения элемента **\<hostInBrowser />** . Если значение **true**, новый элемент **\<hostInBrowser />** включается в элемент **\<entryPoint />** . Включение элемента является накопительным: если элемент **\<hostInBrowser />** уже существует, он не удаляется и не перезаписывается. Вместо этого создается дополнительный элемент **\<hostInBrowser />** . Если задано значение **false**, манифест приложения не изменяется.|

## <a name="remarks"></a>Примечания

 Приложения XBAP запускаются с помощью развертывания ClickOnce и следовательно, должны публиковаться с соответствующими манифестами развертывания и приложения. MSBuild создает манифест приложения с помощью задачи [GenerateApplicationManifest](generateapplicationmanifest-task.md).

 Затем, чтобы настроить приложение для размещения из браузера, необходимо добавить в манифест приложения дополнительный элемент **\<hostInBrowser />** , как показано в примере ниже.

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

 Задача <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> запускается, когда выполняется сборка проекта XBAP для добавления элемента `<hostInBrowser />`.

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

- [Справочные сведения о WPF для MSBuild](../msbuild/wpf-msbuild-reference.md)
- [Справочные сведения о задачах](../msbuild/wpf-msbuild-task-reference.md)
- [Справочные сведения о MSBuild](../msbuild/msbuild-reference.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
- [Создание приложения WPF](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)
- [Общие сведения о приложениях браузера WPF XAML](/dotnet/framework/wpf/app-development/wpf-xaml-browser-applications-overview)
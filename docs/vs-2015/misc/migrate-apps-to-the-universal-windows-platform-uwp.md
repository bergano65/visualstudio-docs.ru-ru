---
title: Перенос приложений на платформу универсальной Windows (UWP) | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5279ab9b-71d9-4be5-81f6-a1f24b06f5fb
caps.latest.revision: 19
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: a23cdd24ad696795127a4469c447f12e9d191930
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49285952"
---
# <a name="migrate-apps-to-the-universal-windows-platform-uwp"></a>Перенос приложений на универсальную платформу Windows (UWP)
Вручную внесите необходимые изменения в существующие файлы проектов для приложений Магазина Windows 8.1, Windows Phone 8.1 или универсальных приложений Windows, созданных с помощью версии-кандидата Visual Studio 2015, чтобы их можно было использовать в окончательной первоначальной версии Visual Studio 2015. (Если у вас есть универсальное приложение Windows 8.1 с проектом приложения Windows и проектом Windows Phone, инструкции по миграции нужно будет выполнить для каждого проекта.)  
  
 Универсальная платформа Windows позволяет создавать приложения, предназначенные для одного или нескольких семейств устройств. Чтобы получить дополнительную информацию об универсальных приложениях Windows, ознакомьтесь с этим [руководством по платформе](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx).  
  
-   [Перенос существующего приложения Магазина Windows 8.1 или приложения для Windows Phone 8.1 на языке C# или Visual Basic](#MigrateCSharp) на универсальную платформу Windows.  
  
-   [Перенос существующего приложения Магазина Windows 8.1 или приложения для Windows Phone 8.1 на языке C++](#MigrateCPlusPlus) на универсальную платформу Windows.  
  
-   [Изменения, которые необходимо внести для существующих универсальных приложений Windows, созданных с помощью версии-кандидата Visual Studio 2015](#PreviousVersions).  
  
-   [Изменения, которые необходимо внести для существующих проектов модульных тестов универсальных приложений Windows, созданных с помощью версии-кандидата Visual Studio 2015](#MigrateUnitTest).  
  
 Если вы не хотите вносить все эти изменения, узнайте, как [перенести существующие приложения](http://msdn.microsoft.com/library/windows/apps/xaml/mt238321.aspx) в новый проект универсального приложения Windows.  
  
##  <a name="MigrateCSharp"></a> Перенос C# и Visual Basic Windows Store 8.1 или Windows Phone 8.1 приложения универсальную платформу Windows  
  
#### <a name="migrate-your-cvb-project-files"></a>Перенос файлов проекта C# или Visual Basic  
  
1.  Чтобы определить установленную универсальную платформу Windows, откройте следующую папку: **\Program Files (x86)\Windows Kits\10\Platforms\UAP**. Она содержит список папок для каждой установленной универсальной платформы Windows. Имя папки соответствует версии установленной универсальной платформы Windows. Например, для устройства с ОС Windows 10 устанавливается универсальная платформа Windows версии 10.0.10240.0.  
  
     ![Откройте папку, чтобы посмотреть установленные версии](../misc/media/uap-uwpversions.png "UAP_UWPVersions")  
  
     Можно установить несколько версий универсальной платформы Windows. Мы рекомендуем использовать последнюю версию для вашего приложения.  
  
2.  Используя проводник, перейдите в папку, где хранится проект UWP. Создайте JSON-файл в этой папке. Назовите файл project.json, а затем добавьте в него следующее содержимое.  
  
    ```json  
    {  
      "dependencies": {  
        "Microsoft.ApplicationInsights": "1.0.0",  
        "Microsoft.ApplicationInsights.PersistenceChannel": "1.0.0",  
        "Microsoft.ApplicationInsights.WindowsApps": "1.0.0",  
        "Microsoft.NETCore.UniversalWindowsPlatform": "5.0.0"  
      },  
      "frameworks": {  
        "uap10.0": {}  
      },  
      "runtimes": {  
        "win10-arm": {},  
        "win10-arm-aot": {},  
        "win10-x86": {},  
        "win10-x86-aot": {},  
        "win10-x64": {},  
        "win10-x64-aot": {}  
      }  
    }  
  
    ```  
  
3.  Создайте файл default.rd.xml с приведенным ниже содержимым. Если у вас есть проект Visual Basic, добавьте этот файл в каталог My Project проекта. Если у вас есть проект C#, добавьте этот файл в каталог Properties проекта.  
  
    ```xml  
    <?xml version="1.0"?>  
    <!-- This file contains Runtime Directives used by .NET Native. The defaults here are suitable for most developers. However, you can modify these parameters to modify the behavior of the .NET Native optimizer. Runtime Directives are documented at http://go.microsoft.com/fwlink/?LinkID=391919 To fully enable reflection for App1.MyClass and all of its public/private members <Type Name="App1.MyClass" Dynamic="Required All"/> To enable dynamic creation of the specific instantiation of AppClass<T> over System.Int32 <TypeInstantiation Name="App1.AppClass" Arguments="System.Int32" Activate="Required Public" /> Using the Namespace directive to apply reflection policy to all the types in a particular namespace <Namespace Name="DataClasses.ViewModels" Seralize="All" /> -->  
    <Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata"><Application>  
    <!-- An Assembly element with Name="*Application*" applies to all assemblies in the application package. The asterisks are not wildcards. -->  
    <Assembly Dynamic="Required All" Name="*Application*"/>  
    <!-- Add your application specific runtime directives here. -->  
    </Application></Directives>  
    ```  
  
4.  Откройте решение, которое содержит существующее приложение Магазина Windows 8.1 или приложение для Windows Phone 8.1, в Visual Studio.  
  
5.  В обозревателе решений щелкните существующий проект приложения правой кнопкой мыши и выберите пункт **Выгрузить проект**. После выгрузки проекта щелкните его файл правой кнопкой мыши еще раз и выберите команду изменения файла CSPROJ или VBPROJ.  
  
     ![Правой кнопкой мыши проект и щелкните "Изменить"](../misc/media/uap-editproject.png "UAP_EditProject")  
  
6.  Найти \<PropertyGroup > элемент, содержащий \<TargetPlatformVersion > со значением 8.1. Выполните следующие действия для этого \<PropertyGroup > элемент:  
  
    1.  Установите для параметра \<платформы > элемента: **x86**.  
  
    2.  Добавить \<TargetPlatformIdentifier > элемент и присвойте ему значение: **UAP**.  
  
    3.  Измените существующее значение \<TargetPlatformVersion > элемента, который будет значение установленной версии универсальной платформы Windows. Кроме того, добавить \<TargetPlatformMinVersion > элемент и присвойте ему то же значение.  
  
    4.  Измените значение свойства \<MinimumVisualStudioVersion > элемента: **14**.  
  
    5.  Замените \<ProjectTypeGuids > элемента, как показано ниже:  
  
         Для C#:  
  
        ```xml  
        <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>  
        ```  
  
         Для Visual Basic:  
  
        ```xml  
        <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{F184B08F-C81C-45F6-A57F-5ABD9991F28F}</ProjectTypeGuids>  
        ```  
  
    6.  Добавить \<EnableDotNetNativeCompatibleProfile > элемент и присвойте ему значение: **true**.  
  
    7.  Масштаб ресурса по умолчанию для универсальных приложений Windows — 200. Если проект включает ресурсы, не масштабируется при 200, необходимо добавить \<UapDefaultAssetScale > со значением, равным масштаб ресурсов элемент PropertyGroup. Узнайте больше о [ресурсах и масштабах](http://msdn.microsoft.com/library/jj679352.aspx).  
  
         Теперь ваш \<PropertyGroup > элемент должен выглядеть как в этом примере:  
  
        ```xml  
        <PropertyGroup>  
            …  
             <Platform Condition=" '$(Platform)' == '' ">x86</Platform>  
             <TargetPlatformVersion>10.0.10240.0</TargetPlatformVersion>  
             <TargetPlatformMinVersion>10.0.10240.0</TargetPlatformMinVersion>  
             <TargetPlatformIdentifier>UAP</TargetPlatformIdentifier>  
             <MinimumVisualStudioVersion>14</MinimumVisualStudioVersion>  
             <ProjectTypeGuids>{A5A43C5B-DE2A-4C0C-9213-0A381AF9435A};{FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}</ProjectTypeGuids>  
        <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>  
             <UapDefaultAssetScale>100</UapDefaultAssetScale>  
             …  
        </PropertyGroup>  
        ```  
  
7.  Замените все вхождения значения 12.0 на значение 14.0 в соответствии с версией Visual Studio, которая теперь используется. Например:  
  
    ```xml  
    <Project Tools Version="14.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    ```  
  
    ```  
    <PropertyGroup Condition=" '$(VisualStudioVersion)' == '' or '$(VisualStudioVersion)' < '14.0' ">  
        <VisualStudioVersion>14.0</VisualStudioVersion>  
    ```  
  
8.  Найти \<PropertyGroup > элементы, настроенные для платформы AnyCPU, в составе атрибута Condition. Удалите эти элементы и все их дочерние элементы. Платформа AnyCPU не поддерживается для приложений Windows 10 в Visual Studio 2015. Например, следует удалить \<PropertyGroup > элементы, такие как следующие:  
  
    ```xml  
    <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">  
        <PlatformTarget>AnyCPU</PlatformTarget>  
        <DebugSymbols>true</DebugSymbols>  
        <DebugType>full</DebugType>  
        <Optimize>false</Optimize>  
        <OutputPath>bin\Debug\</OutputPath>  
        <DefineConstants>DEBUG;TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>  
        <ErrorReport>prompt</ErrorReport>  
        <WarningLevel>4</WarningLevel>  
      </PropertyGroup>  
      <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">  
        <PlatformTarget>AnyCPU</PlatformTarget>  
        <DebugType>pdbonly</DebugType>  
        <Optimize>true</Optimize>  
        <OutputPath>bin\Release\</OutputPath>  
        <DefineConstants>TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>  
        <ErrorReport>prompt</ErrorReport>  
        <WarningLevel>4</WarningLevel>  
      </PropertyGroup>  
    ```  
  
9. Для каждого из оставшихся \<PropertyGroup > Проверьте, если элемент имеет атрибут Condition с конфигурацией выпуска, элемент. Если Да, но он не содержит \<UseDotNetNativeToolchain > элемента, добавьте его. Задайте значение для \<UseDotNetNativeToolchain > элемента значение true, следующим образом:  
  
    ```xml  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|x64'">  
        <OutputPath>bin\x64\Release\</OutputPath>  
        <DefineConstants>TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>  
        <Optimize>true</Optimize>  
        <NoWarn>;2008</NoWarn>  
        <DebugType>pdbonly</DebugType>  
        <PlatformTarget>x64</PlatformTarget>  
        <UseVSHostingProcess>false</UseVSHostingProcess>  
        <ErrorReport>prompt</ErrorReport>  
        <Prefer32Bit>true</Prefer32Bit>  
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>  
      </PropertyGroup>  
    ```  
  
10. Для Windows Phone проектов, удалять только \<PropertyGroup > элемент, содержащий \<TargetPlatformIdentifier > со значением WindowsPhoneApp. Также удалите все его дочерние элементы.  
  
    ```xml  
    <PropertyGroup Condition=" '$(TargetPlatformIdentifier)' == '' ">  
      <TargetPlatformIdentifier>WindowsPhoneApp</TargetPlatformIdentifier>  
    </PropertyGroup>  
    ```  
  
11. Найти \<ItemGroup > элемент, содержащий \<AppxManifest > элемента. Добавьте следующий \<None > как дочерний элемент элемента \<ItemGroup > элемент:  
  
    ```xml  
    <None Include="project.json" />  
    ```  
  
12. Найти \<ItemGroup > элемент, содержащий другие активы, которые добавляются в проект, например PNG-файлы логотипов (\<Content Include="Assets\Logo.scale-100.png» / >). Добавьте следующий \<содержимого > дочерний элемент этого \<ItemGroup > элемент:  
  
     **Для C#:**  
  
    ```xml  
    <Content Include="Properties\default.rd.xml" />  
    ```  
  
     **Для Visual Basic:**  
  
    ```xml  
    <Content Include="My Project\default.rd.xml" />  
    ```  
  
13. Найти \<ItemGroup >, включающий \<ссылку > дочерних элементов на пакеты NuGet. Запишите пакеты NuGet, которые вы использовали, так как их потребуется загрузить с помощью диспетчера пакетов NuGet после перезагрузки проекта. Удалите этот \<ItemGroup > вместе с его дочерних элементов. Например, проект UWP может содержать следующие пакеты NuGet, которые необходимо удалить.  
  
    ```xml  
    <ItemGroup>  
        <Reference Include="Microsoft.ApplicationInsights, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">  
          <HintPath>..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.dll</HintPath>  
          <Private>True</Private>  
        </Reference>  
        <Reference Include="Microsoft.ApplicationInsights.Extensibility.Windows, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">  
          <HintPath>..\packages\Microsoft.ApplicationInsights.WindowsApps.0.14.3-build00177\lib\win81\Microsoft.ApplicationInsights.Extensibility.Windows.dll</HintPath>  
          <Private>True</Private>  
        </Reference>  
        <Reference Include="Microsoft.ApplicationInsights.PersistenceChannel, Version=0.14.3.186, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">  
          <HintPath>..\packages\Microsoft.ApplicationInsights.PersistenceChannel.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.PersistenceChannel.dll</HintPath>  
          <Private>True</Private>  
        </Reference>  
        <Reference Include="System.Numerics.Vectors, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">  
          <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.dll</HintPath>  
          <Private>True</Private>  
        </Reference>  
        <Reference Include="System.Numerics.Vectors.WindowsRuntime, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">  
          <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.WindowsRuntime.dll</HintPath>  
          <Private>True</Private>  
        </Reference>  
      </ItemGroup>  
    ```  
  
14. Сохраните изменения.  
  
15. Закройте файл CSPROJ или VBPROJ.  
  
16. Щелкните проект правой кнопкой мыши в обозревателе решений и выберите в контекстном меню команду "Перезагрузить проект". Все файлы проекта теперь должны отображаться в обозревателе решений.  
  
17. Используйте диспетчер NuGet, чтобы снова добавить в проект пакеты, удаленные в предыдущем шаге.  
  
     Теперь необходимо выполнить инструкции по [обновлению файлов манифеста пакета](#PackageManifest) для всех проектов для Магазина Windows 8.1 и Windows Phone 8.1.  
  
##  <a name="MigrateCPlusPlus"></a> Перенос приложений C++ Windows Store 8.1 или Windows Phone 8.1 для универсальной платформы Windows с использованием  
  
#### <a name="migrate-your-c-project-files"></a>Перенос файлов проекта C++  
  
1.  Чтобы определить установленную универсальную платформу Windows, откройте следующую папку: **\Program Files (x86)\Windows Kits\10\Platforms\UAP**. Она содержит список папок для каждой установленной универсальной платформы Windows. Имя папки соответствует версии установленной универсальной платформы Windows. Например, для устройства с ОС Windows 10 устанавливается универсальная платформа Windows версии 10.0.10240.0.  
  
     ![Откройте папку, чтобы посмотреть установленные версии](../misc/media/uap-uwpversions.png "UAP_UWPVersions")  
  
     Можно установить несколько версий универсальной платформы Windows. Мы рекомендуем использовать последнюю версию для вашего приложения.  
  
2.  Откройте решение, которое содержит существующее приложение Магазина Windows 8.1 или приложение для Windows Phone 8.1 на языке C++, в Visual Studio.  
  
     Щелкните правой кнопкой мыши существующий проект в обозревателе решений и выберите пункт **Выгрузить проект**. После выгрузки проекта щелкните его файл правой кнопкой мыши еще раз и выберите команду изменения файла VCXPROJ.  
  
     ![Справа&#45;щелкните файл проекта и выберите команду редактирования](../misc/media/uap-editcplusproject.png "UAP_EditCPlusProject")  
  
3.  Найти \<PropertyGroup > элемент, содержащий \<ApplicationTypeRevision > со значением 8.1. Выполните следующие действия для этого \<PropertyGroup > элемент:  
  
    1.  Добавить \<WindowsTargetPlatformVersion > элемент и \<WindowsTargetPlatformMinVersion > элемент и присвойте им значение установленной версии универсальной платформы Windows.  
  
    2.  Обновите значение элемента ApplicationTypeRevision с 8.1 до 10.0.  
  
    3.  Измените значение свойства \<MinimumVisualStudioVersion > элемента: 14.  
  
    4.  Добавить \<EnableDotNetNativeCompatibleProfile > элемент и присвойте ему значение: true.  
  
    5.  Масштаб ресурса по умолчанию для универсальных приложений Windows — 200. Если проект включает ресурсы, не масштабируется при 200, необходимо добавить \<UapDefaultAssetScale > со значением, равным масштаб ресурсов элемент PropertyGroup. Узнайте больше о [ресурсах и масштабах](http://msdn.microsoft.com/library/jj679352.aspx).  
  
    6.  Для Windows Phone проекты, измените значение \<ApplicationType > с Windows Phone для Windows Store.  
  
         Теперь ваш \<PropertyGroup > элемент должен выглядеть как в этом примере:  
  
        ```xml  
        <PropertyGroup>  
            …  
                  <WindowsTargetPlatformVersion>10.0.10240.0</WindowsTargetPlatformVersion>  
        <WindowsTargetPlatformMinVersion>10.0.10240.0</WindowsTargetPlatformMinVersion>  
             <ApplicationType>Windows Store</ApplicationType>  
             <ApplicationTypeRevision>10.0</ApplicationTypeRevision>  
             <MinimumVisualStudioVersion>14</MinimumVisualStudioVersion>  
             <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>  
             <UapDefaultAssetScale>100</UapDefaultAssetScale>  
             …  
        </PropertyGroup>  
        ```  
  
4.  Изменение всех экземпляров \<PlatformToolset > значение v140 элемента. Пример:  
  
    ```xml  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">  
        <ConfigurationType>Application</ConfigurationType>  
        <UseDebugLibraries>false</UseDebugLibraries>  
        <WholeProgramOptimization>true</WholeProgramOptimization>  
        <PlatformToolset>v140</PlatformToolset>  
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>  
      </PropertyGroup>  
    ```  
  
5.  Для каждого из оставшихся \<PropertyGroup > Проверьте, если элемент имеет атрибут Condition с конфигурацией выпуска, элемент. Если Да, но он не содержит \<UseDotNetNativeToolchain > элемента, добавьте его. Задайте значение для \<UseDotNetNativeToolchain > элемента значение true, следующим образом:  
  
    ```xml  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|X64'" Label="Configuration">  
        <ConfigurationType>Application</ConfigurationType>  
        <UseDebugLibraries>false</UseDebugLibraries>  
        <WholeProgramOptimization>true</WholeProgramOptimization>  
        <PlatformToolset>v140</PlatformToolset>  
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>  
      </PropertyGroup>  
  
    ```  
  
6.  Сохраните изменения. Закройте файл проекта.  
  
7.  Щелкните файл проекта правой кнопкой мыши в обозревателе решений и выберите в контекстном меню команду "Перезагрузить проект". Все файлы проекта теперь должны отображаться в обозревателе решений.  
  
     Теперь необходимо выполнить инструкции по [обновлению файлов манифеста пакета](#PackageManifest) для всех проектов для Магазина Windows 8.1 и Windows Phone 8.1.  
  
##  <a name="PackageManifest"></a> Обновление файла манифеста пакета для проектов Windows Store 8.1 или Windows Phone 8.1  
 Файл манифеста пакета необходимо обновить для каждого проекта в рамках решения.  
  
#### <a name="update-your-package-manifest-file"></a>Обновление файла манифеста пакета  
  
1.  Откройте файл Package.appxmanifest в проекте. Файл Package.AppxManifest необходимо изменить для каждого проекта приложения Магазина Windows и приложения для Windows Phone.  
  
2.  Необходимо обновить \<пакета > элемент, используя новые схемы в соответствии с типом существующего проекта. Сначала удалите указанные ниже схемы в соответствии с типом проекта (приложение Магазина Windows или приложение для Windows Phone).  
  
     **ПРЕЖНИЙ вариант для проекта Windows Store:** вашей \<пакета > элемент будет выглядеть примерно следующий.  
  
    ```xml  
    <Package  
        xmlns="http://schemas.microsoft.com/appx/2010/manifest"     
        xmlns:m2="http://schemas.microsoft.com/appx/2013/manifest">  
  
    ```  
  
     **ПРЕЖНИЙ вариант для проекта Windows Phone:** вашей \<пакета > элемент будет выглядеть примерно следующий.  
  
    ```xml  
    <Package  
        xmlns="http://schemas.microsoft.com/appx/2010/manifest"     
    xmlns:m2="http://schemas.microsoft.com/appx/2013/manifest"  
    xmlns:m3="http://schemas.microsoft.com/appx/2014/manifest"  
    xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest">  
    ```  
  
     **НОВЫЕ возможности для универсальной платформы Windows:** добавьте приведенные ниже схемы для вашего \<пакета > элемента. Удалите из элементов префиксы идентификаторов пространств имен, связанные со схемами, которые вы удалили. Обновите свойство IgnorableNamespaces, присвоив ему значение uap mp. Новый \<пакета > элемент должен выглядеть примерно следующий.  
  
    ```xml  
    <Package  
        xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"  
        xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10"  
        xmlns:mp="http://schemas.microsoft.com/appx/2014/phone/manifest"  
       IgnorableNamespaces= "uap mp">  
  
    ```  
  
3.  Добавить \<зависимости > дочернего элемента \<пакета > элемента. Затем добавьте \<TargetDeviceFamily > дочерний элемент этого \<зависимости > элемента с атрибутами Name, MinVersion и MaxVersionTested. Присвойте атрибуту Name следующее значение: Windows.Universal. В качестве значений атрибутов MinVersion и MaxVersionTested укажите установленную версию универсальной платформы Windows. Этот элемент должен выглядеть следующим образом:  
  
    ```xml  
    <Dependencies>  
    <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10069.0" MaxVersionTested="10.0.10069.0" />  
    </Dependencies>  
    ```  
  
4.  **Для Windows Store только:** необходимо добавить \<MP: phoneidentity > дочернего элемента \<пакета > элемента. Добавьте атрибуты PhoneProductId и PhonePublisherId. Присвойте атрибуту имеют одинаковое значение атрибута Name в PhoneProductId \<удостоверений > элемента. Присвойте атрибуту PhonePublishedId значение 00000000-0000-0000-0000-000000000000. Пример:  
  
    ```xml  
    <Identity Name="aa3815a1-2d97-4c71-8c99-578135b28cd8" Publisher="CN=xxxxxxxx" Version="1.0.0.0" />   
    <mp:PhoneIdentity PhoneProductId="aa3815a1-2d97-4c71-8c99-578135b28cd8" PhonePublisherId="00000000-0000-0000-0000-000000000000"/>  
    ```  
  
5.  Найти \<предварительные требования > элемент и удалите этот элемент и дочерние элементы, которые он содержит.  
  
6.  Добавить **uap** пространства имен следующим \<ресурсов > элементы: Scale, DXFeatureLevel. Пример:  
  
    ```xml  
    <Resources>  
      <Resource Language="en-us"/>  
     <Resource uap:Scale="180"/>  
     <Resource uap:DXFeatureLevel="dx11"/>  
    </Resources>  
  
    ```  
  
7.  Добавить **uap** пространства имен следующим \<возможность > элементов: documentsLibrary, picturesLibrary, videosLibrary, musicLibrary, enterpriseAuthentication, sharedUserCertificates, removableStorage, встречи и контакты. Пример:  
  
    ```xml  
    <Capabilities>  
      <uap:Capability Name="documentsLibrary"/>  
      <uap:Capability Name="removableStorage"/>  
    </Capabilities>  
  
    ```  
  
8.  Добавить **uap** пространство имен для \<VisualElements > элемент и все его дочерние элементы. Пример:  
  
    ```xml  
    <uap:VisualElements  
        DisplayName="My WWA App"  
        Square150x150Logo="images/150x150.png"  
        Square44x44Logo="images/44x44.png"  
        Description="My WWA App"  
        BackgroundColor="#777777">  
      <uap:SplashScreen Image="images/splash.png"/>  
    </uap:VisualElements>  
  
    ```  
  
     **Только для проектов Магазина Windows.** Названия размеров плитки изменились. Измените атрибуты в \<VisualElements > элемент, чтобы отобразить новую специализирующимся размеров плитки. Размер 70x70 изменен на 71x71, а 30x30 — на 44x44.  
  
     **Прежний вариант** названий размеров плитки:  
  
    ```xml  
    <m2:VisualElements  
        …  
        Square30x30Logo="Assets\SmallLogo.png"  
        …>  
     <m2:DefaultTile  
          …  
          Square70x70Logo="images/70x70.png">  
    </m2:VisualElements>  
  
    ```  
  
     **Новый вариант** названий размеров плитки:  
  
    ```xml  
    <uap:VisualElements  
        …  
        Square44x44Logo="Assets\SmallLogo.png"  
        …>  
     <uap:DefaultTile  
          …  
          Square71x71Logo="images/70x70.png">  
    </uap:VisualElements>  
  
    ```  
  
9. Добавить **uap** пространство имен для \<ApplicationContentUriRules > и все его дочерние элементы. Пример:  
  
    ```xml  
    <uap:ApplicationContentUriRules>  
      <uap:Rule Type="include" Match="https://www.microsoft.com/"/>  
      <uap:Rule Type="exclude" Match="*.pdf"/>  
    </uap:ApplicationContentUriRules>  
  
    ```  
  
10. Добавить **uap** пространства имен следующим \<расширения > элементы и все его дочерние элементы: windows.accountPictureProvide, windows.alarm, windows.appointmentsProvider windows.autoPlayContent,  windows.autoPlayDevice, windows.cachedFileUpdate, windows.cameraSettings, windows.fileOpenPicker, windows.fileTypeAssociation, windows.fileSavePicke, windows.lockScreenCall, windows.printTaskSettings, windows.protocol, windows.search, windows.shareTarget. Пример:  
  
    ```xml  
    <Extensions>  
      <uap:Extension Category="windows.alarm"/>  
      <uap:Extension Category="windows.search" EntryPoint="MyActivateableClassId.baz"/>  
      <uap:Extension Category="windows.protocol">  
        <uap:Protocol Name="mailto" DesiredView="useHalf">  
         <uap:DisplayName>MailTo Protocol</uap:DisplayName>  
        </uap:Protocol>  
      </uap:Extension>  
    </Extensions>  
  
    ```  
  
11. Добавьте пространство имен **uap** в фоновые задачи типа chatMessageNotification. Пример:  
  
    ```xml  
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe">  
     <BackgroundTasks ServerName="MyBackgroundTasks">  
        <uap:Task Type="chatMessageNotification"/>  
      </BackgroundTasks>  
    </Extension>  
  
    ```  
  
12. Измените зависимости платформы. Добавьте имя Publisher ко всем \<PackageDependency > элементов, и укажите атрибут MinVersion, если он еще не указан.  
  
     **СТАРЫЙ:** \<PackageDependency > элемент  
  
    ```xml  
    <Dependencies>  
     <PackageDependency Name="Microsoft.VCLibs.120.00" />  
    </Dependencies>  
  
    ```  
  
     **НОВОЕ:** \<PackageDependency > элемент  
  
    ```xml  
    <Dependencies>  
     <PackageDependency  
          Name="Microsoft.VCLibs.120.00"  
          Publisher="CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US"  
          MinVersion="12.0.30113.0" />  
    </Dependencies>  
  
    ```  
  
     Укажите соответствующие значения Publisher и MinVersion для используемой платформы. Учтите, что в Windows 10 эти имена могут измениться.  
  
13. Замените фоновые задачи типов gattCharacteristicNotification и rfcommConnection задачей типа Bluetooth. Пример:  
  
     **СТАРЫЙ:**  
  
    ```xml  
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe">  
    <BackgroundTasks ServerName="MyBackgroundTasks">  
                <Task Type="rfcommConnection"/>  
               <Task Type="gattCharacteristicNotification"/>  
    </BackgroundTasks>  
    </Extension>  
    ```  
  
     **Новый вариант** с задачей типа Bluetooth:  
  
    ```xml  
    <Extension Category="windows.backgroundTasks" EntryPoint="Fabrikam.BackgroundTask" Executable="MyBackground.exe">  
    <BackgroundTasks ServerName="MyBackgroundTasks">  
               <Task Type="bluetooth"/>  
    </BackgroundTasks>  
    </Extension>  
    ```  
  
14. Замените возможности устройства Bluetooth bluetooth.rfcomm и bluetooth.genericAttributeProfile универсальной возможностью Bluetooth. Пример:  
  
     **СТАРЫЙ:**  
  
    ```xml  
    <Capabilities>  
      <m2:DeviceCapability Name="bluetooth.rfcomm">  
        <m2:Device Id="any">  
         <m2:Function Type="serviceId:34B1CF4D-1069-4AD6-89B6-E161D79BE4D8"/>  
        </m2:Device>  
      </m2:DeviceCapability>  
      <m2:DeviceCapability Name="bluetooth.genericAttributeProfile">  
        <m2:Device Id="any">  
         <m2:Function Type="name:heartRate"/>  
        </m2:Device>  
      </m2:DeviceCapability>  
    </Capabilities>  
    ```  
  
     **Новый вариант** с универсальной возможностью Bluetooth:  
  
    ```xml  
    <Capabilities>  
      <uap:DeviceCapability Name="bluetooth"/>  
    </Capabilities>  
  
    ```  
  
15. Удалите все нерекомендуемые элементы.  
  
    1.  Эти атрибуты для \<VisualElements > являются устаревшими. они должны быть удалены:  
  
        -   \<VisualElements > атрибуты: ForegroundText, toastcapable;  
  
        -   \<DefaultTile > атрибут DefaultSize  
  
        -   \<ApplicationView > элемент  
  
         Пример:  
  
        ```xml  
        <m2:VisualElements  
            …  
            ForegroundText="dark"  
            ToastCapable="true">  
        <m2:DefaultTile DefaultSize="square150x150Logo"/>  
          <m2:ApplicationView MinWidth="width320"/>  
        </m2:VisualElements>  
  
        ```  
  
    2.  Удалите расширения Windows.contact и windows.contactPicker, а также все содержащиеся в них элементы.  
  
16. Сохраните файл Package.appxmanifest. Закройте Visual Studio.  
  
17. Прежде чем повторно открывать решение, необходимо удалить некоторые скрытые файлы.  
  
    1.  Откройте проводник, на панели инструментов нажмите **Вид** и выберите пункты **Скрытые элементы** и **Расширения имен файлов**. Откройте следующую папку на компьютере: \<путь к папке решения >\\.vs\\{имя проекта} \v14. Если есть файл с расширением SUO, удалите его.  
  
    2.  Теперь вернитесь к папке, в которой находится решение. Откройте папки проектов, имеющихся в решении. Если внутри этих папок есть файлы с расширением CSPROJ.USER или VBPROJ.USER, удалите их.  
  
         Теперь решение можно повторно открыть в Visual Studio. Можно приступать к написанию кода, сборке и отладке приложения с помощью универсальной платформы Windows.  
  
         Узнайте, как [адаптировать код](https://msdn.microsoft.com/library/windows/apps/dn954974.aspx) для использования новых возможностей универсальной платформы Windows.  
  
##  <a name="PreviousVersions"></a> Изменения, необходимые для существующих универсальных Windows-приложений, созданных с помощью Visual Studio 2015 RC  
 Если вы создали универсальные приложения для Windows 10 с помощью версии-кандидата Visual Studio 2015, проект необходимо изменить так, чтобы он использовал версию универсальной платформы Windows, установленную с последним выпуском Visual Studio 2015. Предыдущие версии не поддерживаются. Необходимые изменения различаются в зависимости от языка, на котором было создано приложение:  
  
-   [Приложения на языке C# и Visual Basic](#RCUpdate10CSharp)  
  
-   [В приложениях C++](#RCUpdate10CPlusPlus)  
  
###  <a name="RCUpdate10CSharp"></a> Обновление проектов C# и Visual Basic для использования последней версии универсальной платформы Windows  
 При открытии решения существующего приложения вы увидите, что приложение требуется обновить.  
  
 ![Просмотр проекта в обозревателе решений](../misc/media/uwp-updaterequired.png "UWP_UpdateRequired")  
  
 Если вы выберете перезагрузку этого проекта в обозревателе решений, появится следующее диалоговое окно.  
  
 ![Перенастройка приложения для использования правильного пакета SDK](../misc/media/missingsdkforuap.png "MissingSDKforUAP")  
  
 Так как пакет SDK универсальной платформы Windows для вашего проекта больше не поддерживается, вы не сможете установить его. Просто нажмите кнопку "ОК" и выполните описанные ниже действия.  
  
##### <a name="update-your-cvb-projects-to-use-the-latest-universal-windows-platform"></a>Обновление проектов C# и Visual Basic для использования последней версии универсальной платформы Windows  
  
1.  Чтобы определить установленную универсальную платформу Windows, откройте следующую папку: **\Program Files (x86)\Windows Kits\10\Platforms\UAP**. Она содержит список папок для каждой установленной универсальной платформы Windows. Имя папки соответствует версии установленной универсальной платформы Windows. Например, для устройства с ОС Windows 10 устанавливается универсальная платформа Windows версии 10.0.10240.0.  
  
     ![Откройте папку, чтобы посмотреть установленные версии](../misc/media/uap-uwpversions.png "UAP_UWPVersions")  
  
     Можно установить несколько версий универсальной платформы Windows. Мы рекомендуем использовать последнюю версию для вашего приложения.  
  
2.  Используя проводник, перейдите в папку, где хранится проект UWP. Удалите файл packages.config и создайте новый JSON-файл в этой папке. Назовите файл project.json, а затем добавьте в него следующее содержимое.  
  
    ```json  
  
    {  
      "dependencies": {  
        "Microsoft.ApplicationInsights": "1.0.0",  
        "Microsoft.ApplicationInsights.PersistenceChannel": "1.0.0",  
        "Microsoft.ApplicationInsights.WindowsApps": "1.0.0",  
        "Microsoft.NETCore.UniversalWindowsPlatform": "5.0.0"  
      },  
      "frameworks": {  
        "uap10.0": {}  
      },  
      "runtimes": {  
        "win10-arm": {},  
        "win10-arm-aot": {},  
        "win10-x86": {},  
        "win10-x86-aot": {},  
        "win10-x64": {},  
        "win10-x64-aot": {}  
      }  
    }  
  
    ```  
  
3.  В Visual Studio откройте решение, содержащее универсальное приложение Windows на языке C# или VB. Вы увидите, что файл проекта (CSPROJ или VBPROJ) необходимо обновить. Щелкните файл проекта правой кнопкой мыши и выберите команду редактирования.  
  
     ![Правой кнопкой мыши проект и щелкните "Изменить"](../misc/media/uap-editproject.png "UAP_EditProject")  
  
4.  Найти \<PropertyGroup > элемент, содержащий \<TargetPlatformVersion > и \<TargetPlatformMinVersion > элементы. Измените существующее значение \<TargetPlatformVersion > и \<TargetPlatformMinVersion > элементы находятся в той же версии универсальной платформы Windows, который вы установили.  
  
     Масштаб ресурса по умолчанию для универсальных приложений Windows — 200. Проекты, созданные с помощью Visual Studio 2015 RC включены ресурсы с масштабом 100, нужно будет добавить \<UapDefaultAssetScale > со значением, равным 100 элемент PropertyGroup. Узнайте больше о [ресурсах и масштабах](http://msdn.microsoft.com/library/jj679352.aspx).  
  
5.  При добавлении ссылок на пакет SDK расширения UWP (например, Windows Mobile SDK) потребуется обновить версию пакета SDK. Например, это \<SDKReference > элемент:  
  
    ```xml  
    <SDKReference Include="WindowsMobile, Version=10.0.0.1">  
          <Name>Microsoft Mobile Extension SDK for Universal App Platform</Name>  
    </SDKReference>  
  
    ```  
  
     необходимо заменить этим:  
  
    ```xml  
    <SDKReference Include="WindowsMobile, Version=10.0.10240.0">  
          <Name>Microsoft Mobile Extension SDK for Universal App Platform</Name>  
    </SDKReference>  
  
    ```  
  
6.  Найти \<целевой > элемент с атрибутом, имеющим значение: EnsureNuGetPackageBuildImports. Удалите этот элемент и все его дочерние элементы.  
  
    ```xml  
    <Target Name="EnsureNuGetPackageBuildImports" BeforeTargets="PrepareForBuild">  
        <PropertyGroup>  
          <ErrorText>This project references NuGet package(s) that are missing on this computer. Use NuGet Package Restore to download them.  For more information, see http://go.microsoft.com/fwlink/?LinkID=322105. The missing file is {0}.</ErrorText>  
        </PropertyGroup>  
        <Error Condition="!Exists('..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets')" Text="$([System.String]::Format('$(ErrorText)', '..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets'))" />  
        <Error Condition="!Exists('..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets')" Text="$([System.String]::Format('$(ErrorText)', '..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets'))" />  
    </Target>  
    ```  
  
7.  Поиск и удаление \<импорта > элементы с атрибутами Project и Condition, ссылающими на Microsoft.Diagnostics.Tracing.EventSource и Microsoft.ApplicationInsights, следующим образом:  
  
    ```xml  
    <Import Project="..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets" Condition="Exists('..\packages\Microsoft.Diagnostics.Tracing.EventSource.Redist.1.1.16-beta\build\portable-net45+win8+wpa81\Microsoft.Diagnostics.Tracing.EventSource.Redist.targets')" />  
    <Import Project="..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets" Condition="Exists('..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\build\portable-win81+wpa81\Microsoft.ApplicationInsights.targets')" />  
  
    ```  
  
8.  Найти \<ItemGroup >, содержащее \<ссылку > дочерних элементов на пакеты NuGet. Запишите пакеты NuGet, на которые имеются ссылки, так как эти сведения потребуются для следующей процедуры. Одно важное отличие форматов проектов для Windows 10 между версией-кандидатом Visual Studio 2015 и окончательной первоначальной версией Visual Studio 2015 RTM заключается в том, что в последней версии используется формат [NuGet](http://docs.nuget.org/) версии 3.  
  
     Удалить \<ItemGroup > и все его дочерние узлы. Например, проект UWP, созданный в версии-кандидате Visual Studio, будет содержать следующие пакеты NuGet, которые необходимо удалить.  
  
    ```xml  
    <ItemGroup>  
        <Reference Include="Microsoft.ApplicationInsights, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">  
          <HintPath>..\packages\Microsoft.ApplicationInsights.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.dll</HintPath>  
          <Private>True</Private>  
        </Reference>  
        <Reference Include="Microsoft.ApplicationInsights.Extensibility.Windows, Version=0.14.3.177, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">  
          <HintPath>..\packages\Microsoft.ApplicationInsights.WindowsApps.0.14.3-build00177\lib\win81\Microsoft.ApplicationInsights.Extensibility.Windows.dll</HintPath>  
          <Private>True</Private>  
        </Reference>  
        <Reference Include="Microsoft.ApplicationInsights.PersistenceChannel, Version=0.14.3.186, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL">  
          <HintPath>..\packages\Microsoft.ApplicationInsights.PersistenceChannel.0.14.3-build00177\lib\portable-win81+wpa81\Microsoft.ApplicationInsights.PersistenceChannel.dll</HintPath>  
          <Private>True</Private>  
        </Reference>  
        <Reference Include="System.Numerics.Vectors, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">  
          <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.dll</HintPath>  
          <Private>True</Private>  
        </Reference>  
        <Reference Include="System.Numerics.Vectors.WindowsRuntime, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">  
          <HintPath>..\packages\System.Numerics.Vectors.4.0.0\lib\win8\System.Numerics.Vectors.WindowsRuntime.dll</HintPath>  
          <Private>True</Private>  
        </Reference>  
      </ItemGroup>  
  
    ```  
  
9. Найти \<ItemGroup > элемент, содержащий \<AppxManifest > элемента. Если имеется \<None > элемент с атрибутом Include: packages.config, удалите его. Кроме того, добавьте \<None > элемент с включаемый атрибут и присвойте ему значение: project.json.  
  
10. Сохраните изменения. Закройте файл проекта.  
  
11. Щелкните файл проекта правой кнопкой мыши в обозревателе решений и выберите в контекстном меню команду "Перезагрузить проект". Все файлы проекта теперь должны отображаться в обозревателе решений.  
  
12. В обозревателе решений выберите файл ApplicationInsights.config и откройте его свойства. Задайте для свойства "Действие сборки" значение "Содержание", а для свойства "Копировать в выходной каталог" значение "Копировать, если новее".  
  
13. Откройте файл Package.appxmanifest в проекте.  
  
    1.  Найти \<TargetDeviceFamily > элемента. В качестве значений атрибутов MinVersion и MaxVersionTested укажите установленную версию универсальной платформы Windows. Пример:  
  
        ```xml  
        <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10240.0" />  
        ```  
  
    2.  Сохраните изменения.  
  
14. Используйте диспетчер NuGet, чтобы добавить пакеты, удаленные в предыдущем шаге. Одно важное отличие форматов проектов для Windows 10 между версией-кандидатом Visual Studio 2015 и окончательной первоначальной версией Visual Studio 2015 RTM заключается в том, что в последней версии используется формат [NuGet](http://docs.nuget.org/) версии 3.  
  
 Теперь можно приступать к написанию кода, сборке и отладке приложения.  
  
 При наличии проектов модульных тестов для универсальных приложений Windows необходимо также выполнить [эти действия](#MigrateUnitTest).  
  
###  <a name="RCUpdate10CPlusPlus"></a> Обновление проектов C++ для использования последней версии универсальной платформы Windows  
  
1.  Чтобы определить установленную универсальную платформу Windows, откройте следующую папку: **\Program Files (x86)\Windows Kits\10\Platforms\UAP**. Она содержит список папок для каждой установленной универсальной платформы Windows. Имя папки соответствует версии установленной универсальной платформы Windows. Например, для устройства с ОС Windows 10 устанавливается универсальная платформа Windows версии 10.0.10240.0.  
  
     ![Откройте папку, чтобы посмотреть установленные версии](../misc/media/uap-uwpversions.png "UAP_UWPVersions")  
  
     Можно установить несколько версий универсальной платформы Windows. Мы рекомендуем использовать последнюю версию для вашего приложения.  
  
2.  Откройте решение, содержащее универсальное приложение Windows на языке C++. Щелкните правой кнопкой мыши VCXPROJ-файл проекта и выберите команду его выгрузки. После выгрузки проекта щелкните его файл правой кнопкой мыши еще раз и выберите команду изменения файла.  
  
     ![Выгрузить проект, а затем измените файл проекта](../misc/media/uap-editearliercplus.png "UAP_EditEarlierCPlus")  
  
3.  Найти какой-либо \<PropertyGroup > элементов, которые не содержат атрибут Condition, но содержат \<ApplicationTypeRevision > элемента. Обновите значение ApplicationTypeRevision с 8.2 до 10.0. Добавить \<WindowsTargetPlatformVersion > и \<WindowsTargetPlatformMinVersion > элемент и задать их значения, то значение установленной версии универсальной платформы Windows.  
  
     Добавить \<EnableDotNetNativeCompatibleProfile > элемент и присвойте ему значение true, если элемент еще не существует.  
  
     Масштаб ресурса по умолчанию для универсальных приложений Windows — 200. Проекты, созданные с помощью Visual Studio 2015 RC включены ресурсы с масштабом 100, нужно будет добавить \<UapDefaultAssetScale > со значением, равным 100 элемент PropertyGroup. Узнайте больше о [ресурсах и масштабах](http://msdn.microsoft.com/library/jj679352.aspx).  
  
     Поэтому эта \<PropertyGroup > элемент теперь будет примерно следующим:  
  
    ```xml  
    <PropertyGroup Label="Globals">  
        …  
        <MinimumVisualStudioVersion>14.0</MinimumVisualStudioVersion>  
        <ApplicationType>Windows Store</ApplicationType>  
        <ApplicationTypeRevision>10.0</ApplicationTypeRevision>  
        <WindowsTargetPlatformVersion>10.0.10240.0</WindowsTargetPlatformVersion>  
        <WindowsTargetPlatformMinVersion>10.0.10240.0</WindowsTargetPlatformMinVersion>  
        <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>  
        <UapDefaultAssetScale>100</UapDefaultAssetScale>  
      </PropertyGroup>  
  
    ```  
  
4.  Для каждого из оставшихся \<PropertyGroup > Проверьте, если элемент имеет атрибут Condition с конфигурацией выпуска, элемент. Если Да, но он не содержит \<UseDotNetNativeToolchain > элемента, добавьте его. Задайте значение для \<UseDotNetNativeToolchain > элемента значение true, следующим образом:  
  
    ```xml  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|Win32'" Label="Configuration">  
        <ConfigurationType>Application</ConfigurationType>  
        <UseDebugLibraries>false</UseDebugLibraries>  
        <WholeProgramOptimization>true</WholeProgramOptimization>  
        <PlatformToolset>v140</PlatformToolset>  
        <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>  
      </PropertyGroup>  
  
    ```  
  
5.  Необходимо обновить \<EnableDotNetNativeCompatibleProfile > элемент и \<UseDotNetNativeToolchain > элемент для включения .NET Native и .NET Native не включен в шаблонах C++.  
  
     Сохраните изменения. Закройте файл проекта.  
  
6.  Щелкните файл проекта правой кнопкой мыши в обозревателе решений и выберите в контекстном меню команду "Перезагрузить проект". Все файлы проекта теперь должны отображаться в обозревателе решений.  
  
7.  Откройте файл Package.appxmanifest в проекте.  
  
    1.  Найти \<TargetDeviceFamily > элемента. В качестве значений атрибутов MinVersion и MaxVersionTested укажите установленную версию универсальной платформы Windows. Пример:  
  
        ```xml  
        <TargetDeviceFamily Name="Windows.Universal" MinVersion="10.0.10240.0" MaxVersionTested="10.0.10240.0" />  
        ```  
  
    2.  Сохраните изменения.  
  
         Теперь можно приступать к написанию кода, сборке и отладке приложения.  
  
         При наличии проектов модульных тестов для универсальных приложений Windows необходимо также выполнить [эти действия](#MigrateUnitTest).  
  
##  <a name="MigrateUnitTest"></a> Изменения, необходимые для существующих проектов модульных тестов для универсальных Windows-приложений, созданных с помощью Visual Studio 2015 RC  
 Если вы создавали проекты модульных тестов для универсальных приложений Windows 10 с помощью версии-кандидата Visual Studio 2015, в файлы проектов необходимо внести следующие дополнительные изменения, чтобы такие проекты тестов можно было использовать в последнем выпуске Visual Studio 2015. Необходимые изменения различаются в зависимости от языка, на котором было создано приложение:  
  
-   [Приложения на языке C# и Visual Basic](#UnitTestRCUpdate10CSharp)  
  
-   [В приложениях C++](#UnitTestRCUpdate10CPlusPlus)  
  
###  <a name="UnitTestRCUpdate10CSharp"></a> Обновление проектов модульных тестов C# и Visual Basic  
  
1.  В Visual Studio откройте решение, содержащее проект модульного теста C# или VB. Измените значение свойства \<OuttputType > элемента: AppContainerExe.  
  
    ```xml  
  
    <OutputType>AppContainerExe</OutputType>  
  
    ```  
  
2.  Замените этот элемент \<EnableCoreRuntime > false\</EnableCoreRuntime > следующим элементом:  
  
    ```xml  
  
    <EnableDotNetNativeCompatibleProfile>true</EnableDotNetNativeCompatibleProfile>  
  
    ```  
  
3.  Удалите следующие строки.  
  
    ```xml  
  
    <PropertyGroup>  
        <AppXPackage>True</AppXPackage>  
        <AppxPackageIncludePrivateSymbols>true</AppxPackageIncludePrivateSymbols>  
     </PropertyGroup>  
     <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Debug|AnyCPU' ">  
     <PlatformTarget>AnyCPU</PlatformTarget>  
     <DebugSymbols>true</DebugSymbols>  
     <DebugType>full</DebugType>  
     <Optimize>false</Optimize>  
     <OutputPath>bin\Debug\</OutputPath>  
     <DefineConstants>DEBUG;TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>  
     <ErrorReport>prompt</ErrorReport>  
     <WarningLevel>4</WarningLevel>  
     </PropertyGroup>  
     <PropertyGroup Condition=" '$(Configuration)|$(Platform)' == 'Release|AnyCPU' ">  
        <PlatformTarget>AnyCPU</PlatformTarget>  
        <DebugType>pdbonly</DebugType>  
        <Optimize>true</Optimize>  
        <OutputPath>bin\Release\</OutputPath>  
        <DefineConstants>TRACE;NETFX_CORE;WINDOWS_UAP</DefineConstants>  
        <ErrorReport>prompt</ErrorReport>  
        <WarningLevel>4</WarningLevel>  
     </PropertyGroup>  
  
    ```  
  
4.  Добавьте этот элемент \<UseDotNetNativeToolchain > true\</UseDotNetNativeToolchain > как дочерний элемент в следующие группы свойств:  
  
    ```xml  
  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|ARM'">  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|X86'">  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)' == 'Release|X64'">  
  
    ```  
  
5.  Удалить следующий \<ItemGroup > элементы:  
  
    ```xml  
  
    <ItemGroup>  
       <Compile Include="Properties\AssemblyInfo.cs" />  
       <Compile Include="UnitTest.cs" />  
    </ItemGroup>  
    <ItemGroup>  
       <AppxManifest Include="Package.appxmanifest">  
          <SubType>Designer</SubType>  
       </AppxManifest>  
       <None Include="packages.config" />  
       <None Include="UnitTestProject1_TemporaryKey.pfx" />  
    </ItemGroup>  
    <ItemGroup>  
       <Content Include="Properties\Default.rd.xml" />  
       <Content Include="Assets\Logo.scale-240.png" />  
       <Content Include="Assets\SmallLogo.scale-240.png" />  
       <Content Include="Assets\SplashScreen.scale-240.png" />  
       <Content Include="Assets\Square71x71Logo.scale-240.png" />  
       <Content Include="Assets\StoreLogo.scale-240.png" />  
       <Content Include="Assets\WideLogo.scale-240.png" />  
    </ItemGroup>  
  
    ```  
  
     Замените их следующими элементами.  
  
    ```xml  
  
    <ItemGroup>  
       <Compile Include="Properties\AssemblyInfo.cs" />  
       <Compile Include="UnitTestApp.xaml.cs">  
          <DependentUpon>UnitTestApp.xaml</DependentUpon>  
       </Compile>  
       <Compile Include="UnitTest.cs" />  
    </ItemGroup>  
    <ItemGroup>  
       <ApplicationDefinition Include="UnitTestApp.xaml">  
          <Generator>MSBuild:Compile</Generator>  
          <SubType>Designer</SubType>  
       </ApplicationDefinition>  
    </ItemGroup>  
    <ItemGroup>  
       <AppxManifest Include="Package.appxmanifest">  
          <SubType>Designer</SubType>  
       </AppxManifest>  
       <None Include="UnitTestProject1_TemporaryKey.pfx" />  
    </ItemGroup>  
    <ItemGroup>  
       <Content Include="Properties\UnitTestApp.rd.xml" />  
       <Content Include="Assets\LockScreenLogo.scale-200.png" />  
       <Content Include="Assets\SplashScreen.scale-200.png" />  
       <Content Include="Assets\Square150x150Logo.scale-200.png" />  
       <Content Include="Assets\Square44x44Logo.scale-200.png" />  
       <Content Include="Assets\Square44x44Logo.targetsize-24_altform-unplated.png" />  
       <Content Include="Assets\StoreLogo.png" />  
       <Content Include="Assets\Wide310x150Logo.scale-200.png" />  
    </ItemGroup>  
    ```  
  
6.  Создайте новый проект модульного теста и скопируйте файлы UnitTestApp.xaml и UnitTestApp.xaml.cs из нового проекта в существующий обновляемый проект модульного теста.  
  
7.  Скопируйте файл UnitTestApp.rd.xml из папки Properties нового проекта модульного теста в папку Properties существующего обновляемого проекта модульного теста.  
  
8.  Откройте файл Package.appxmanifest в проекте. Затем удалите из него следующие элементы.  
  
    ```xml  
  
    <Applications>  
       <Application Id="vstest.executionengine.universal.App"  
             Executable="vstest.executionengine.appcontainer.uap.exe"  
             EntryPoint="Microsoft.VisualStudio.TestPlatform.TestExecutor.AppContainer.App">  
          <uap:VisualElements  
             DisplayName="UnitTestProject1"  
             Square150x150Logo="Assets\Logo.png"  
             Square44x44Logo="Assets\SmallLogo.png"  
             Description="UnitTestProject1"  
             BackgroundColor="#464646">  
             <uap:SplashScreen Image="Assets\SplashScreen.png" />  
          </uap:VisualElements>  
       </Application>  
    </Applications>  
    <Capabilities>  
       <Capability Name="internetClientServer" />  
    </Capabilities>  
    ```  
  
     Замените удаленные элементы следующими элементами. Вместо UnitTestProject1 укажите соответствующее значение ProjectName в зависимости от имени проекта в элементах, перечисленных ниже.  
  
    ```xml  
  
    <Applications>  
       <Application Id="vstest.executionengine.universal.App"   
             Executable="$targetnametoken$.exe"  
             EntryPoint="UnitTestProject1.App">  
          <uap:VisualElements  
                DisplayName="UnitTestProject1"  
                Square150x150Logo="Assets\Square150x150Logo.png"  
                Square44x44Logo="Assets\Square44x44Logo.png"  
                Description="UnitTestProject1"  
                BackgroundColor="transparent">  
             <uap:DefaultTile Wide310x150Logo="Assets\Wide310x150Logo.png"/>  
             <uap:SplashScreen Image="Assets\SplashScreen.png" />  
          </uap:VisualElements>  
       </Application>  
    </Applications>  
    <Capabilities>  
       <Capability Name="internetClient" />  
    </Capabilities>  
    ```  
  
 Теперь можно выполнить модульные тесты.  
  
###  <a name="UnitTestRCUpdate10CPlusPlus"></a> Обновление проектов C++ для использования последней версии универсальной платформы Windows  
  
1.  В Visual Studio откройте решение, содержащее проект модульного теста C++. Удалите следующие элементы.  
  
    ```xml  
  
    <TestApplication>true</TestApplication>  
    <AppxPackage>True</AppxPackage>  
    <CppWindowsStoreUnitTestLibraryType>true</CppWindowsStoreUnitTestLibraryType>  
    <EnableCoreRuntime>false</EnableCoreRuntime>  
  
    ```  
  
2.  Добавьте следующий \<ProjectConfiguration > под ним этот элемент \<ItemGroup Label = «ProjectConfigurations» > Если они отсутствуют в данном файле:  
  
    ```xml  
  
    <ProjectConfiguration Include="Debug|x64">  
       <Configuration>Debug</Configuration>  
       <Platform>x64</Platform>  
    </ProjectConfiguration>  
    <ProjectConfiguration Include="Release|x64">  
       <Configuration>Release</Configuration>  
       <Platform>x64</Platform>  
    </ProjectConfiguration>  
  
    ```  
  
3.  Замените все вхождения этого элемента:  
  
    ```xml  
  
    <ConfigurationType>DynamicLibrary</ConfigurationType>  
  
    ```  
  
     На следующий код:  
  
    ```xml  
  
    <ConfigurationType>Application</ConfigurationType>  
  
    ```  
  
4.  Добавьте следующие \<PropertyGroup > элементов, если они отсутствуют в файле:  
  
    ```xml  
  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Debug|x64'" Label="Configuration">  
       <ConfigurationType>Application</ConfigurationType>  
       <UseDebugLibraries>true</UseDebugLibraries>  
       <PlatformToolset>v140</PlatformToolset>  
    </PropertyGroup>  
    <PropertyGroup Condition="'$(Configuration)|$(Platform)'=='Release|x64'" Label="Configuration">  
       <ConfigurationType>Application</ConfigurationType>  
       <UseDebugLibraries>false</UseDebugLibraries>  
       <WholeProgramOptimization>true</WholeProgramOptimization>  
       <PlatformToolset>v140</PlatformToolset>  
       <UseDotNetNativeToolchain>true</UseDotNetNativeToolchain>  
    </PropertyGroup>  
  
    ```  
  
5.  Замените все вхождения этого элемента:  
  
    ```xml  
  
    <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include;$(ProjectDir);$(IntermediateOutputPath);%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>  
    ```  
  
     На следующий код:  
  
    ```xml  
  
    <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include\UWP;$(ProjectDir);$(IntermediateOutputPath);%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>  
  
    ```  
  
6.  Замените все вхождения этого элемента:  
  
    ```xml  
  
    <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\Lib;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>  
  
    ```  
  
     На следующий код:  
  
    ```xml  
  
    <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\lib\UWP;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>  
  
    ```  
  
7.  Добавьте следующие \<ItemDefinitionGroup > элементов в соответствующем разделе, который уже содержит другие \<ItemDefinitionGroup > элементы:  
  
    ```xml  
  
    <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Debug|x64'">  
       <ClCompile>  
          <AdditionalOptions>/bigobj %(AdditionalOptions)</AdditionalOptions>  
          <DisableSpecificWarnings>4453;28204</DisableSpecificWarnings>  
          <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include\UWP;$(ProjectDir);$(IntermediateOutputPath);%     (AdditionalIncludeDirectories)</AdditionalIncludeDirectories>  
       </ClCompile>  
    <Link>  
       <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\lib\UWP;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>  
    </Link>  
    </ItemDefinitionGroup>  
    <ItemDefinitionGroup Condition="'$(Configuration)|$(Platform)'=='Release|x64'">  
       <ClCompile>  
          <AdditionalOptions>/bigobj %(AdditionalOptions)</AdditionalOptions>  
          <DisableSpecificWarnings>4453;28204</DisableSpecificWarnings>  
          <AdditionalIncludeDirectories>$(VCInstallDir)UnitTest\include\UWP;$(ProjectDir);$(IntermediateOutputPath);%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>  
       </ClCompile>  
       <Link>  
          <AdditionalLibraryDirectories>$(VCInstallDir)UnitTest\lib\UWP;%(AdditionalLibraryDirectories)</AdditionalLibraryDirectories>  
       </Link>  
    </ItemDefinitionGroup>  
  
    ```  
  
8.  Удалить следующий \< ItemGroup > элемент:  
  
    ```xml  
  
    <ItemGroup>  
       <Image Include="Assets\Logo.scale-100.png" />  
       <Image Include="Assets\SmallLogo.scale-100.png" />  
       <Image Include="Assets\StoreLogo.scale-100.png" />  
       <Image Include="Assets\SplashScreen.scale-100.png" />  
       <Image Include="Assets\WideLogo.scale-100.png" />  
    </ItemGroup>  
  
    ```  
  
     Замените это \<ItemGroup > элемент:  
  
    ```xml  
  
    <ItemGroup>  
       <Image Include="Assets\LockScreenLogo.scale-200.png" />  
       <Image Include="Assets\SplashScreen.scale-200.png" />  
       <Image Include="Assets\Square44x44Logo.scale-200.png" />  
       <Image Include="Assets\Square44x44Logo.targetsize-24_altform-unplated.png" />  
       <Image Include="Assets\Square150x150Logo.scale-200.png" />  
       <Image Include="Assets\StoreLogo.png" />  
       <Image Include="Assets\Wide310x150Logo.scale-200.png" />  
    </ItemGroup>  
  
    ```  
  
9. Удалить следующий \< ItemGroup > элемент:  
  
    ```xml  
  
    <ItemGroup>  
       <ClInclude Include="pch.h" />  
    </ItemGroup>  
    ```  
  
     Замените эти \<ItemGroup > элементы:  
  
    ```xml  
  
    <ItemGroup>  
       <ClInclude Include="pch.h" />  
       <ClInclude Include="UnitTestApp.xaml.h">  
          <DependentUpon>UnitTestApp.xaml</DependentUpon>  
       </ClInclude>  
    </ItemGroup>  
    <ItemGroup>  
       <ApplicationDefinition Include="UnitTestApp.xaml">  
          <SubType>Designer</SubType>  
       </ApplicationDefinition>  
    </ItemGroup>  
  
    ```  
  
10. Удалите следующий элемент:  
  
    ```xml  
    <ClCompile Include="UnitTest.cpp"/>  
    ```  
  
     Замените эти \<CICompile > элементы:  
  
    ```xml  
  
    <ClCompile Include="UnitTestApp.xaml.cpp">  
       <DependentUpon>UnitTestApp.xaml</DependentUpon>  
    </ClCompile>  
    <ClCompile Include="UnitTest.cpp"/>  
  
    ```  
  
11. Добавьте этот элемент:  
  
    ```xml  
    <Import Project="$(VCTargetsPath)\Microsoft.Cpp.targets" />  
    ```  
  
     над этим элементом в файле:  
  
    ```xml  
  
    <ItemGroup>  
       <Xml Include="UnitTestApp.rd.xml" />  
    </ItemGroup>  
    ```  
  
12. Создайте новый проект модульного теста C++ и скопируйте файлы UnitTestApp.xaml, UnitTestApp.xaml.cpp, UnitTestApp.xaml.h и UnitTestApp.rd.xml из этого проекта в существующий обновляемый проект.  
  
13. Откройте файл Package.appxmanifest в проекте. Затем удалите из него следующие элементы.  
  
    ```xml  
  
    <Applications>  
       <Application Id="vstest.executionengine.universal.App"  
             Executable="vstest.executionengine.appcontainer.uap.exe"  
             EntryPoint="Microsoft.VisualStudio.TestPlatform.TestExecutor.AppContainer.App">  
          <uap:VisualElements  
             DisplayName="UnitTestProject1"  
             Square150x150Logo="Assets\Logo.png"  
             Square44x44Logo="Assets\SmallLogo.png"  
             Description="UnitTestProject1"  
             BackgroundColor="#464646">  
             <uap:SplashScreen Image="Assets\SplashScreen.png" />  
          </uap:VisualElements>  
       </Application>  
    </Applications>  
    <Capabilities>  
       <Capability Name="internetClientServer" />  
    </Capabilities>  
  
    ```  
  
     Замените удаленные элементы следующими элементами. Вместо UnitTestProject1 укажите соответствующее значение ProjectName в зависимости от имени проекта в элементах, перечисленных ниже.  
  
    ```xml  
  
    <Applications>  
       <Application Id="vstest.executionengine.universal.App"   
                Executable="$targetnametoken$.exe"  
                EntryPoint="UnitTestProject1.App">  
          <uap:VisualElements  
                DisplayName="UnitTestProject1"  
                Square150x150Logo="Assets\Square150x150Logo.png"  
                Square44x44Logo="Assets\Square44x44Logo.png"  
                Description="UnitTestProject1"  
                BackgroundColor="transparent">  
                <uap:DefaultTile Wide310x150Logo="Assets\Wide310x150Logo.png"/>  
                <uap:SplashScreen Image="Assets\SplashScreen.png" />  
          </uap:VisualElements>  
       </Application>  
    </Applications>  
    <Capabilities>  
       <Capability Name="internetClient" />  
    </Capabilities>  
  
    ```
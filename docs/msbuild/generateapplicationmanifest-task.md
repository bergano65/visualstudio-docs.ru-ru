---
title: "Задача GenerateApplicationManifest | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#GenerateApplicationManifest"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "GenerateApplicationManifest - задача [MSBuild]"
  - "HostInBrowser - свойство (MSBuild)"
  - "MSBuild, GenerateApplicationManifest - задача"
ms.assetid: a494102b-0cb2-4755-8e2a-d2c0f39fac1d
caps.latest.revision: 24
caps.handback.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Задача GenerateApplicationManifest
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Создание манифеста приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] или собственного манифеста.  Собственный манифест описывает компонент посредством определения уникального идентификатора для этого компонента и определения всех сборок и файлов, образующих этот компонент.  Манифест приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] расширяет собственный манифест посредством указания точки входа и уровня безопасности этого приложения.  
  
## Параметры  
 В следующей таблице описаны параметры задачи `GenerateApplicationManifest`.  
  
|Параметр|Описание|  
|--------------|--------------|  
|`AssemblyName`|Необязательный параметр типа `String`.<br /><br /> Задает поле `Name` удостоверения сборки для создаваемого манифеста.  Если этот параметр не задан, то имя выводится из параметра `EntryPoint` или `InputManifest`.  Если создать имя невозможно, задача оповещает об ошибке.|  
|`AssemblyVersion`|Необязательный параметр типа `String`.<br /><br /> Поле `Version` удостоверения сборки для создаваемого манифеста.  Если этот параметр не указан, используется значение по умолчанию, равное "1.0.0.0".|  
|`ClrVersion`|Необязательный параметр типа `String`.<br /><br /> Минимальный номер версии среды CLR, необходимой для приложения.  По умолчанию используется номер версии среды CLR, применяемой в системе построения.  Если задача создает собственный манифест, данный параметр игнорируется.|  
|`ConfigFile`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Элемент, в котором содержится файл конфигурации приложения.  Если задача создает собственный манифест, данный параметр игнорируется.|  
|`Dependencies`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Список элементов, определяющий набор зависимых сборок для созданного манифеста.  Каждый элемент можно дополнительно описать в метаданных и указать дополнительное состояние развертывания и тип зависимости.  Дополнительные сведения см. далее в разделе "Метаданные элементов".|  
|`Description`|Необязательный параметр типа `String`.<br /><br /> Описание приложения или компонента.|  
|`EntryPoint`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Один элемент, указывающий точку входа для создаваемой сборки манифеста.<br /><br /> Для манифеста приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] этот параметр указывает сборку, которая запускается при запуске приложения.|  
|`ErrorReportUrl`|Необязательный параметр типа [String](assetId:///String?qualifyHint=False&autoUpgrade=True).<br /><br /> задает URL\-адрес веб\-страницы, который отображается в диалоговых окнах во время отчетов об ошибках во время установки ClickOnce.|  
|`FileAssociations`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Задает список из одного или нескольких типов файлов, связанных с манифестом развертывания ClickOnce.<br /><br /> Связи файла действительны, только если требуемой версией .NET Framework является 3.5 или более поздняя.|  
|`Files`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Файлы, включаемые в манифест.  Необходимо указать полный путь к каждому файлу.|  
|`HostInBrowser`|Необязательный параметр типа [Boolean](assetId:///Boolean?qualifyHint=False&autoUpgrade=True).<br /><br /> Если `true`, приложение размещается в браузере \(как WPF\-приложения браузера\).|  
|`IconFile`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Файл значка приложения.  Значок приложения описан в созданном манифесте приложения и используется в меню "Пуск" и в диалоговом окне "Установка и удаление программ".  Если этот входной параметр не определен, используется значок по умолчанию.  Если задача создает собственный манифест, данный параметр игнорируется.|  
|`InputManifest`|Необязательный параметр типа <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Входной XML\-документ, на основе которого создается манифест.  Он позволяет переносить в результирующий манифест такие структурные данные, как сведения о безопасности приложений и настраиваемые определения манифеста.  Корневой элемент в XML\-документе должен быть узлом сборки в пространстве имен asmv1.|  
|`IsolatedComReferences`|Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Компоненты COM, изолируемые в создаваемом манифесте.  Этот параметр обеспечивает поддержку изолированных компонентов COM для развертывания с использованием COM\-компонентов без регистрации.  Он позволяет автоматически создать манифест со стандартными определениями регистрации COM.  Для реализации этой возможности необходимо, чтобы компоненты COM были зарегистрированы на компьютере построения.|  
|`ManifestType`|Необязательный параметр типа `String`.<br /><br /> Тип создаваемого манифеста.  Этот параметр может принимать следующие значения:<br /><br /> -   `Native`<br />-   `ClickOnce`<br /><br /> Если этот параметр не указан, то задача использует значение по умолчанию `ClickOnce`.|  
|`MaxTargetPath`|Необязательный параметр типа `String`.<br /><br /> Максимально допустимая длина пути к файлу при развертывании приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] .  Если это значение указано, то с ним сверяется длина каждого пути к файлу в приложении.  Если какие\-либо элементы превышают предел, выдается предупреждение проверки построения.  Если этот входной параметр не определен или равен нулю, то проверка не выполняется.  Если задача создает собственный манифест, данный параметр игнорируется.|  
|`OSVersion`|Необязательный параметр типа `String`.<br /><br /> Минимальный номер версии операционной системы, необходимой для приложения.  Например, значение "5.1.2600.0" соответствует Windows XP.  Если значение этого параметра не задано, используется значение "4.10.0.0" для операционной системы Windows 98 Second Edition, соответствующей минимальным требованиям платформы .NET Framework.  Если задача создает собственный манифест, данный входной параметр игнорируется.|  
|`OutputManifest`|Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Указывает имя созданного файла результатов манифеста.  Если этот параметр не задан, то имя выходного файла выводится из удостоверения созданного манифеста.|  
|`Platform`|Необязательный параметр типа `String`.<br /><br /> Определяет имя целевой платформы приложения.  Этот параметр может принимать следующие значения:<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> Если этот параметр не указан, то задача использует значение по умолчанию `AnyCPU`.|  
|`Product`|Необязательный параметр типа `String`.<br /><br /> Указывает имя приложения.  Если этот параметр не задан, то имя файла результата выводится из удостоверения созданного манифеста.  Это имя используется для имени ярлыка в меню Пуск и является частью имени, которое появляется в диалоговом окне Установка или удаление программ.|  
|`Publisher`|Необязательный параметр типа `String`.<br /><br /> Указывает имя издателя приложения.  Если этот параметр не задан, то имя выводится из имени зарегистрированного пользователя или из удостоверения созданного манифеста.  Это имя используется для имени папки в меню Пуск и является частью имени, которое появляется в диалоговом окне Установка или удаление программ.|  
|`RequiresMinimumFramework35SP1`|Необязательный параметр типа `Boolean`.<br /><br /> Если значение равно true, приложение требует .NET Framework 3.5 SP1 или более поздней версии.|  
|`TargetCulture`|Необязательный параметр типа `String`.<br /><br /> Язык и региональные параметры приложения, а также значение в поле `Language` удостоверения сборки для созданного манифеста.  Если этот параметр не задан, то предполагается, что язык и региональные параметры приложения универсальны.|  
|`TargetFrameworkMoniker`|Необязательный параметр типа assetId:///String?qualifyHint=False&autoUpgrade=True.<br /><br /> Определяет моникер требуемой версии .NET Framework.|  
|`TargetFrameworkProfile`|Необязательный параметр типа assetId:///String?qualifyHint=False&autoUpgrade=True.<br /><br /> Задает профиль целевой платформы.|  
|`TargetFrameworkSubset`|Необязательный параметр типа assetId:///String?qualifyHint=False&autoUpgrade=True.<br /><br /> Определяет имя требуемого подмножества .NET Framework.|  
|`TargetFrameworkVersion`|Необязательный параметр типа assetId:///String?qualifyHint=False&autoUpgrade=True.<br /><br /> Указывает профиль целевой платформы .NET Framework для проекта.|  
|`TrustInfoFile`|Необязательный параметр типа <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> XML\-документ, в котором задан уровень безопасности приложения.  Корневой элемент в XML\-документе должен быть узлом trustInfo в пространстве имен asmv2.  Если задача создает собственный манифест, данный параметр игнорируется.|  
|`UseApplicationTrust`|Необязательный параметр типа assetId:///Boolean?qualifyHint=False&autoUpgrade=True.<br /><br /> Если true, свойства `Product`, `Publisher` и `SupportUrl` записываются в манифест приложения.|  
  
## Заметки  
 Помимо параметров, которые перечислены выше, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.GenerateManifestBase>, который наследует от класса <xref:Microsoft.Build.Utilities.Task>.  Список параметров класса Task см. в описании класса [Базовый класс Task](../msbuild/task-base-class.md).  
  
 Сведения об использовании задачи `GenerateDeploymentManifest` см. в [GenerateApplicationManifest Task](../msbuild/generateapplicationmanifest-task.md).  
  
 Для каждого из входных параметров зависимостей и файлов можно дополнительно указать состояние развертывания в метаданных элементов.  
  
## Метаданные элементов  
  
|Имя метаданных|Описание|  
|--------------------|--------------|  
|`DependencyType`|Эти метаданные указывают на то, что зависимость публикуется и устанавливается вместе с приложением либо относится к предварительным требованиям.  Эти метаданные допустимы для всех зависимостей, но не используются для файлов.  Для этих метаданных доступны следующие значения:<br /><br /> -   `Install`<br />-   `Prerequisite`<br /><br /> Значение по умолчанию — Install.|  
|`AssemblyType`|Эти метаданные указывают на то, что зависимость является управляемой или собственной сборкой.  Эти метаданные допустимы для всех зависимостей, но не используются для файлов.  Для этих метаданных доступны следующие значения:<br /><br /> -   `Managed`<br />-   `Native`<br />-   `Unspecified`<br /><br /> Значение по умолчанию — `Unspecified`. Оно показывает, что при создании манифеста тип сборки определится автоматически.|  
|`Group`|Группа для загрузки дополнительных файлов по требованию.  Имя группы определяется приложением и может быть любой строкой.  Пустая строка означает, что файл не входит в группу загрузки \(по умолчанию\).  Файлы, не включенные в группу, входят в исходную загрузку приложения.  Файлы, включенные в группу, загружаются только по явному запросу приложения с использованием пространства имен <xref:System.Deployment.Application>.<br /><br /> Эти метаданные допустимы для всех файлов, где в `IsDataFile` указано `false`, и всех зависимостей, где в `DependencyType` указано `Install`.|  
|`TargetPath`|Способ определения пути в создаваемом манифесте.  Этот атрибут действителен для всех файлов.  Если данный атрибут не определен, используется спецификация элементов.  Этот атрибут действителен для всех файлов и зависимостей, где в `DependencyType` указано `Install`.|  
|`IsDataFile`|Значение типа `Boolean`, показывающее, является ли файл файлом данных.  Особенность файла данных в том, что он переносится при обновлениях приложения.  Эти метаданные применимы только для файлов.  `False` является значением по умолчанию.|  
  
## Пример  
 В этом примере задача `GenerateApplicationManifest` используется для создания манифеста приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], а задача `GenerateDeploymentManifest` — для создания манифеста развертывания приложения с одной сборкой.  Затем используется задача `SignFile` для подписи манифестов.  
  
 Этот пример является иллюстрацией простейшего возможного сценария создания манифестов, где манифесты [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] создаются для одной программы.  Имя и идентификатор по умолчанию выводятся из сборки для данного манифеста.  
  
> [!NOTE]
>  В приведенном ниже примере все двоичные файлы приложений собраны заранее, чтобы сосредоточить внимание на создании манифестов.  В этом примере представлено полностью работоспособное развертывание [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
> [!NOTE]
>  Дополнительные сведения о свойстве `Thumbprint`, которое используется в задаче `SignFile` данного примера, см. в разделе [Задача SignFile](../msbuild/signfile-task.md).  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <Thumbprint>  
             <!-- Insert generated thumbprint here -->  
        </Thumbprint>  
    </PropertyGroup>  
  
    <Target Name="Build">  
  
        <GenerateApplicationManifest  
            EntryPoint="@(EntryPoint)">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
        <GenerateDeploymentManifest  
            EntryPoint="@(ApplicationManifest)">  
            <Output  
                ItemName="DeployManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateDeploymentManifest>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(ApplicationManifest)"/>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(DeployManifest)"/>  
  
    </Target>  
</Project>  
```  
  
## Пример  
 В этом примере используются задачи `GenerateApplicationManifest` и `GenerateDeploymentManifest` для создания манифестов приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] и развертывания для приложения с одной сборкой, и указываются имя и удостоверение манифестов.  
  
 Этот пример аналогичен предыдущему за исключением того, что имя и удостоверение заданы явно.  Кроме того, этот пример настроен как интернет\-приложение, а не как установленное приложение.  
  
> [!NOTE]
>  В приведенном ниже примере все двоичные файлы приложений собраны заранее, чтобы сосредоточить внимание на создании манифестов.  В этом примере представлено полностью работоспособное развертывание [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
> [!NOTE]
>  Дополнительные сведения о свойстве `Thumbprint`, которое используется в задаче `SignFile` данного примера, см. в разделе [Задача SignFile](../msbuild/signfile-task.md).  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <Thumbprint>  
             <!-- Insert generated thumbprint here -->  
        </Thumbprint>  
    </PropertyGroup>  
  
    <Target Name="Build">  
  
        <GenerateApplicationManifest  
            AssemblyName="SimpleWinApp.exe"  
            AssemblyVersion="1.0.0.0"  
            EntryPoint="@(EntryPoint)"  
            OutputManifest="SimpleWinApp.exe.manifest">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
        <GenerateDeploymentManifest  
                AssemblyName="SimpleWinApp.application"  
                AssemblyVersion="1.0.0.0"  
                EntryPoint="@(ApplicationManifest)"  
                Install="false"  
                OutputManifest="SimpleWinApp.application">  
                <Output  
                    ItemName="DeployManifest"  
                    TaskParameter="OutputManifest"/>  
        </GenerateDeploymentManifest>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(ApplicationManifest)"/>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(DeployManifest)"/>  
  
    </Target>  
</Project>  
```  
  
## Пример  
 В этом примере используются задачи `GenerateApplicationManifest` и `GenerateDeploymentManifest` для создания манифестов приложения [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] и развертывания для приложения с несколькими файлами и сборками.  
  
> [!NOTE]
>  В приведенном ниже примере все двоичные файлы приложений собраны заранее, чтобы сосредоточить внимание на создании манифестов.  В этом примере представлено полностью работоспособное развертывание [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
> [!NOTE]
>  Дополнительные сведения о свойстве `Thumbprint`, которое используется в задаче `SignFile` данного примера, см. в разделе [Задача SignFile](../msbuild/signfile-task.md).  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <Thumbprint>  
             <!-- Insert generated thumbprint here -->  
        </Thumbprint>  
        <DeployUrl>  
            <!-- Insert the deployment URL here -->  
        </DeployUrl>  
        <SupportUrl>  
            <!-- Insert the support URL here -->  
        </SupportUrl>  
    </PropertyGroup>  
  
    <Target Name="Build">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe"/>  
        <Dependency Include="ClassLibrary1.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Install</DependencyType>  
        </Dependency>  
        <Dependency Include="ClassLibrary2.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Install</DependencyType>  
            <Group>Secondary</Group>  
        </Dependency>  
        <Dependency Include="MyAddIn1.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Install</DependencyType>  
            <TargetPath>Addins\MyAddIn1.dll</TargetPath>  
        </Dependency>  
        <Dependency Include="ClassLibrary3.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Prerequisite</DependencyType>  
        </Dependency>  
  
        <File Include="Text1.txt">  
            <TargetPath>Text\Text1.txt</TargetPath>  
            <Group>Text</Group>  
        </File>  
        <File Include="DataFile1.xml ">  
            <TargetPath>Data\DataFile1.xml</TargetPath>  
            <IsDataFile>true</IsDataFile>  
        </File>  
  
        <IconFile Include="Heart.ico"/>  
        <ConfigFile Include="app.config">  
            <TargetPath>SimpleWinApp.exe.config</TargetPath>  
        </ConfigFile>  
        <BaseManifest Include="app.manifest"/>  
    </ItemGroup>  
  
    <Target Name="Build">  
  
        <GenerateApplicationManifest  
            AssemblyName="SimpleWinApp.exe"  
            AssemblyVersion="1.0.0.0"  
            ConfigFile="@(ConfigFile)"  
            Dependencies="@(Dependency)"  
            Description="TestApp"  
            EntryPoint="@(EntryPoint)"  
            Files="@(File)"  
            IconFile="@(IconFile)"  
            InputManifest="@(BaseManifest)"  
            OutputManifest="SimpleWinApp.exe.manifest">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
        <GenerateDeploymentManifest  
            AssemblyName="SimpleWinApp.application"  
            AssemblyVersion="1.0.0.0"  
            DeploymentUrl="$(DeployToUrl)"  
            Description="TestDeploy"  
            EntryPoint="@(ApplicationManifest)"  
            Install="true"  
            OutputManifest="SimpleWinApp.application"  
            Product="SimpleWinApp"  
            Publisher="Microsoft"  
            SupportUrl="$(SupportUrl)"  
            UpdateEnabled="true"  
            UpdateInterval="3"  
            UpdateMode="Background"  
            UpdateUnit="weeks">  
            <Output  
                ItemName="DeployManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateDeploymentManifest>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(ApplicationManifest)"/>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(DeployManifest)"/>  
  
    </Target>  
</Project>  
```  
  
## Пример  
 В этом примере используется задача `GenerateApplicationManifest` для создания собственного манифеста приложения Test.exe, ссылающегося на собственный компонент Alpha.dll и изолированный COM\-компонент Bravo.dll.  
  
 В этом примере на выходе получается манифест Test.exe.manifest, позволяющий развертывать приложение, скопированное командой XCOPY, то есть использовать COM\-компоненты без регистрации.  
  
> [!NOTE]
>  В приведенном ниже примере все двоичные файлы приложений собраны заранее, чтобы сосредоточить внимание на создании манифестов.  В этом примере представлено полностью работоспособное развертывание [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
```  
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <File Include="Test.exe" />  
        <Dependency Include="Alpha.dll">  
            <AssemblyType>Native</AssemblyType>  
            <DependencyType>Install</DependencyType>  
        </Dependency>  
        <ComComponent Include="Bravo.dll" />  
    </ItemGroup>  
  
    <Target Name="Build">  
        <GenerateApplicationManifest  
            AssemblyName="Test.exe"  
            AssemblyVersion="1.0.0.0"  
            Dependencies="@(Dependency)"  
            Files="@(File)"  
            IsolatedComReferences="@(ComComponent)"  
            ManifestType="Native">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
    </Target>  
</Project>  
```  
  
## См. также  
 [Задачи](../msbuild/msbuild-tasks.md)   
 [Задача GenerateDeploymentManifest](../msbuild/generatedeploymentmanifest-task.md)   
 [Задача SignFile](../msbuild/signfile-task.md)   
 [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)
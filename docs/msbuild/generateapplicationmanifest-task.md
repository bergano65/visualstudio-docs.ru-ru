---
title: Задача GenerateApplicationManifest | Документы Майкрософт
description: Используйте задачу GenerateApplicationManifest MSBuild для создания манифеста приложения ClickOnce или нативного манифеста.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#GenerateApplicationManifest
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, GenerateApplicationManifest task
- HostInBrowser property (MSBuild)
- GenerateApplicationManifest task [MSBuild]
ms.assetid: a494102b-0cb2-4755-8e2a-d2c0f39fac1d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2af490f27ab1cdecfe57da9253aff6c4247c7223
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914882"
---
# <a name="generateapplicationmanifest-task"></a>GenerateApplicationManifest - задача

Создает манифест приложения ClickOnce или собственный манифест. Собственный манифест описывает компонент, определяя для него уникальный идентификатор, а также идентифицируя все составляющие компонент сборки и файлы. Манифест приложения ClickOnce расширяет собственный манифест, задавая точку входа приложения и его уровень безопасности.

## <a name="parameters"></a>Параметры

В следующей таблице приводятся параметры для задачи `GenerateApplicationManifest`.

| Параметр | Описание |
|---------------------------------| - |
| `AssemblyName` | Необязательный параметр `String`.<br /><br /> Указывает поле `Name` удостоверения сборки для создаваемого манифеста. Если этот параметр не задан, то имя выводится из параметра `EntryPoint` или `InputManifest`. Если создать имя не удается, задача сообщает об ошибке. |
| `AssemblyVersion` | Необязательный параметр `String`.<br /><br /> Указывает поле `Version` удостоверения сборки для создаваемого манифеста. Если параметр не указан, используется имя по умолчанию "1.0.0.0". |
| `ClrVersion` | Необязательный параметр `String`.<br /><br /> Указывает минимальную версию среды CLR, необходимую приложению. Значение по умолчанию — версия среды CLR, используемая системой сборки. Если задача создает собственный манифест, этот параметр игнорируется. |
| `ConfigFile` | Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает элемент, содержащий файл конфигурации приложения. Если задача создает собственный манифест, этот параметр игнорируется. |
| `Dependencies` | Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает список элементов, который определяет набор независимых сборок для созданного манифеста. Каждый элемент может быть дополнительно описан в метаданных, чтобы указать дополнительное состояние развертывания и тип зависимости. Дополнительные сведения см. в разделе [Метаданные элементов](#item-metadata). |
| `Description` | Необязательный параметр `String`.<br /><br /> Указывает описание для приложения или компонента. |
| `EntryPoint` | Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Задает отдельный элемент, указывающий точку входа для создаваемой сборки манифеста.<br /><br /> Для манифеста приложения ClickOnce этот параметр указывает сборку, которая выполняется при запуске приложения. |
| `ErrorReportUrl` | Необязательный параметр <xref:System.String?displayProperty=fullName>.<br /><br /> Указывает URL-адрес веб-страницы, который отображается в диалоговых окнах отчетов об ошибках во время установок ClickOnce. |
| `FileAssociations` | Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Задает список из одного или нескольких типов файлов, сопоставленных с манифестом развертывания ClickOnce.<br /><br /> Сопоставления файлов действительны только при ориентации на платформу .NET Framework 3.5 или более поздней версии. |
| `Files` | Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Включаемые в манифест файлы. Укажите полный путь для каждого файла. |
| `HostInBrowser` | Необязательный параметр <xref:System.Boolean>.<br /><br /> Если `true`, приложение размещается в браузере (как приложения веб-браузера WPF). |
| `IconFile` | Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает файл значка приложения. Значок приложения задается в создаваемом манифесте приложения и используется для **меню "Пуск"** и диалогового окна **Установка и удаление программ**. Если этот входной параметр не указан, используется значок по умолчанию. Если задача создает собственный манифест, этот параметр игнорируется. |
| `InputManifest` | Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Указывает входной XML-документ, который служит основой для генератора манифеста. Это позволяет структурированным данным, например определениям безопасности приложений или пользовательским определениям манифестов, отражаться в выходном манифесте. Корневой элемент в XML-документе должен быть узлом сборки в пространстве имен asmv1. |
| `IsolatedComReferences` | Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>`[]` .<br /><br /> Указывает COM-компоненты, которые нужно изолировать в создаваемом манифесте. Этот параметр позволяет изолировать COM-компоненты для развертывания "COM без регистрации". Это работает за счет автоматического создания манифеста со стандартными определениями регистрации COM. Однако для правильной работы этой функции COM-компоненты нужно регистрировать на компьютере сборки. |
| `ManifestType` | Необязательный параметр `String`.<br /><br /> Указывает тип создаваемого манифеста. Этот параметр может иметь следующие значения:<br /><br /> -   `Native`<br />-   `ClickOnce`<br /><br /> Если этот параметр не задан, задача использует значение по умолчанию `ClickOnce`. |
| `MaxTargetPath` | Необязательный параметр `String`.<br /><br /> Определяет максимально допустимую длину пути к файлу при развертывании приложения ClickOnce. Если это значение указано, то с ним сверяется длина каждого пути к файлу в приложении. Любые элементы, превышающие это ограничение, вызовут предупреждение сборки. Если это значение не определено или равно нулю, то проверка не выполняется. Если задача создает собственный манифест, этот параметр игнорируется. |
| `OSVersion` | Необязательный параметр `String`.<br /><br /> Указывает минимально возможную версию операционной системы (ОС), необходимую для приложения. Например, значение "5.1.2600.0" означает, что используется операционная система Windows XP. Если этот параметр не задан, используется значение "4.10.0.0", обозначающее Windows 98 Second Edition — минимальную версию ОС, поддерживаемую платформой .NET Framework. Если задача создает собственный манифест, этот входной параметр игнорируется. |
| `OutputManifest` | Необязательный выходной параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Указывает имя создаваемого выходного файла манифеста. Если этот параметр не задан, имя выходного файла выводится из идентификатора создаваемого манифеста. |
| `Platform` | Необязательный параметр `String`.<br /><br /> Указывает целевую платформу приложения. Этот параметр может иметь следующие значения:<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> Если этот параметр не задан, задача использует значение по умолчанию `AnyCPU`. |
| `Product` | Необязательный параметр `String`.<br /><br /> Указывает имя приложения. Если этот параметр не задан, имя выводится из идентификатора создаваемого манифеста. Это имя используется в качестве имени ярлыка в меню **Пуск** и является частью имени, которое отображается в диалоговом окне **Установка и удаление программ**. |
| `Publisher` | Необязательный параметр `String`.<br /><br /> Указывает имя издателя приложения. Если этот параметр не задан, имя выводится из имени зарегистрированного пользователя или из идентификатора создаваемого манифеста. Это имя используется в качестве имени папки в меню **Пуск** и является частью имени, которое отображается в диалоговом окне **Установка и удаление программ**. |
| `RequiresMinimumFramework35SP1` | Необязательный параметр `Boolean`.<br /><br /> Если задано значение true, приложению требуется платформа .NET Framework 3.5 с пакетом обновления 1 (SP1) или более поздней версии. |
| `TargetCulture` | Необязательный параметр `String`.<br /><br /> Идентифицирует язык и региональные параметры приложения и указывает поле `Language` удостоверения сборки для создаваемого манифеста. Если этот параметр не задан, то предполагается, что в приложении не изменяются язык и региональные параметры. |
| `TargetFrameworkMoniker` | Необязательный параметр `String`.<br /><br /> Задает моникер целевой платформы. |
| `TargetFrameworkProfile` | Необязательный параметр `String`.<br /><br /> Задает профиль целевой платформы. |
| `TargetFrameworkSubset` | Необязательный параметр `String`.<br /><br /> Задает имя целевого подмножества платформы .NET Framework. |
| `TargetFrameworkVersion` | Необязательный параметр `String`.<br /><br /> Задает целевую платформу .NET Framework проекта. |
| `TrustInfoFile` | Необязательный параметр <xref:Microsoft.Build.Framework.ITaskItem>.<br /><br /> Задает XML-документ, указывающий уровень безопасности приложения. Корневой элемент в XML-документе должен быть узлом trustInfo в пространстве имен asmv2. Если задача создает собственный манифест, этот параметр игнорируется. |
| `UseApplicationTrust` | Необязательный параметр `Boolean`.<br /><br /> Если задано значение true, свойства `Product`, `Publisher` и `SupportUrl` записываются в манифест приложения. |

## <a name="remarks"></a>Примечания

Помимо перечисленных выше параметров, эта задача наследует параметры от класса <xref:Microsoft.Build.Tasks.GenerateManifestBase>, который, в свою очередь, наследует от класса <xref:Microsoft.Build.Utilities.Task>. Список параметров класса Task см. в статье [Базовый класс Task](../msbuild/task-base-class.md).

Сведения об использовании задачи `GenerateDeploymentManifest` см. в разделе [Задача GenerateApplicationManifest](../msbuild/generateapplicationmanifest-task.md).

Входные параметры для зависимостей и файлов можно дополнительно декорировать метаданными элементов, чтобы указать состояние развертывания для каждого из элементов.

## <a name="item-metadata"></a>Метаданные элементов

|Имя метаданных|Описание|
|-------------------|-----------------|
|`DependencyType`|Указывает, публикуется и устанавливается ли зависимость с приложением или необходимым условием. Эти метаданные допустимы для всех зависимостей, но не используются для файлов. Допустимые значения для этих метаданных:<br /><br /> -   `Install`<br />-   `Prerequisite`<br /><br /> Значение по умолчанию — Install.|
|`AssemblyType`|Указывает, является ли зависимость управляемой или машинной сборкой. Эти метаданные допустимы для всех зависимостей, но не используются для файлов. Допустимые значения для этих метаданных:<br /><br /> -   `Managed`<br />-   `Native`<br />-   `Unspecified`<br /><br /> Значение `Unspecified` используется по умолчанию и указывает, что манифест определяет тип сборки автоматически.|
|`Group`|Указывает группу для скачивания дополнительных файлов по запросу. Имя группы определяется приложением и может быть любой строкой. Пустая строка указывает, что файл не является частью группы скачивания, используемой по умолчанию. Файлы, не входящие в группу, относятся к начальным скачиваемым данным для приложения. Файлы в группе скачиваются при явном запросе приложением с помощью <xref:System.Deployment.Application>.<br /><br /> Эти метаданные допустимы для всех файлов, где `IsDataFile` имеет значение `false`, и всех зависимостей, где `DependencyType` имеет значение `Install`.|
|`TargetPath`|Указывает, как требуется определить путь в создаваемом манифесте. Этот атрибут допустим для всех файлов. Если атрибут не задан, используется спецификация элемента. Этот атрибут допустим для всех файлов и зависимостей, для которых `DependencyType` имеет значение `Install`.|
|`IsDataFile`|Значение метаданных `Boolean`, указывающее, является ли этот файл файлом данных. Файл данных имеет особенность — он перемещается между обновлениями приложения. Эти метаданные допустимы только для файлов. `False` является значением по умолчанию.|

## <a name="example-1"></a>Пример 1

Этот пример использует задачу `GenerateApplicationManifest`, чтобы создать манифест приложения ClickOnce, и задачу `GenerateDeploymentManifest`, чтобы создать манифест развертывания для приложения с одной сборкой. Затем он использует задачу `SignFile` для подписи манифестов.

Это иллюстрирует самый простой сценарий создания манифестов, где манифесты ClickOnce создаются для одной программы. Для манифеста удостоверение и имя по умолчанию наследуются от сборки.

> [!NOTE]
> В приведенном ниже примере все двоичные файлы приложения собраны заранее, чтобы сосредоточить внимание на создании манифестов. В этом примере создается полностью работоспособное развертывание ClickOnce.
>
> [!NOTE]
> Дополнительные сведения о свойстве `Thumbprint`, используемом для задачи `SignFile` в этом примере, см. в разделе [Задача SignFile](../msbuild/signfile-task.md).

```xml
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

## <a name="example-2"></a>Пример 2

Этот пример использует задачи `GenerateApplicationManifest` и `GenerateDeploymentManifest`, чтобы создать манифесты развертывания и приложения ClickOnce для приложения с одной сборкой, задавая при этом имя и удостоверение манифестов.

Этот пример похож на предыдущий, за исключением того, что имя и удостоверение манифестов указываются явно. Кроме того, этот пример настраивается как интерактивное, а не установленное приложение.

> [!NOTE]
> В приведенном ниже примере все двоичные файлы приложения собраны заранее, чтобы сосредоточить внимание на создании манифестов. В этом примере создается полностью работоспособное развертывание ClickOnce.
>
> [!NOTE]
> Дополнительные сведения о свойстве `Thumbprint`, используемом для задачи `SignFile` в этом примере, см. в разделе [Задача SignFile](../msbuild/signfile-task.md).

```xml
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

## <a name="example-3"></a>Пример 3

Этот пример использует задачи `GenerateApplicationManifest` и `GenerateDeploymentManifest`, чтобы создать манифесты развертывания и приложения ClickOnce для приложения с несколькими файлами и сборками.

> [!NOTE]
> В приведенном ниже примере все двоичные файлы приложения собраны заранее, чтобы сосредоточить внимание на создании манифестов. В этом примере создается полностью работоспособное развертывание ClickOnce.
>
> [!NOTE]
> Дополнительные сведения о свойстве `Thumbprint`, используемом для задачи `SignFile` в этом примере, см. в разделе [Задача SignFile](../msbuild/signfile-task.md).

```xml
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

## <a name="example-4"></a>Пример 4

Этот пример использует задачу `GenerateApplicationManifest`, чтобы создать собственный манифест для приложения *Test.exe*, ссылаясь на собственный компонент *Alpha.dll* и изолированный COM-компонент *Bravo.dll*.

Этот пример создает *Test.exe.manifest*, делая приложение развертываемым посредством XCOPY с помощью преимущества COM без регистрации.

> [!NOTE]
> В приведенном ниже примере все двоичные файлы приложения собраны заранее, чтобы сосредоточить внимание на создании манифестов. В этом примере создается полностью работоспособное развертывание ClickOnce.

```xml
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

## <a name="see-also"></a>См. также

- [Задачи](../msbuild/msbuild-tasks.md)
- [GenerateDeploymentManifest - задача](../msbuild/generatedeploymentmanifest-task.md)
- [SignFile - задача](../msbuild/signfile-task.md)
- [Справочные сведения о задачах](../msbuild/msbuild-task-reference.md)

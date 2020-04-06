---
title: Обновление пользовательских шаблонов проектов и элементов для Visual Studio 2017
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 5f807e142b376d05e5a44600e8f6b24ddb3593be
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698849"
---
# <a name="upgrade-custom-project-and-item-templates-for-visual-studio-2017"></a>Обновление пользовательских проектов и элементов шаблоны для визуальной студии 2017

Начиная с Visual Studio 2017, Visual Studio обнаруживает шаблоны проектов и элементов, которые были установлены .vsix или .msi по-другому, чем предыдущие версии Visual Studio. Если у вас есть расширения, которые используют пользовательские шаблоны проекта или элемента, вам нужно обновить расширения. В этой статье объясняется, что вы должны сделать.

Это изменение затрагивает только Visual Studio 2017. Это не влияет на предыдущие версии Visual Studio.

Если вы хотите создать шаблон проекта или элемента в рамках расширения VSIX, [см.](../extensibility/creating-custom-project-and-item-templates.md)

## <a name="template-scanning"></a>Сканирование шаблонов

В предыдущих версиях Visual Studio, **devenv /setup** или **devenv /installvstemplates** сканировали локальный диск, чтобы найти шаблоны проекта и элемента. Начиная с Visual Studio 2017, сканирование выполняется только для расположения пользовательского уровня. Местоположение на уровне пользователя по умолчанию **составляет % USERPROFILE% -Документы\\<версии\>Visual Studio .Templates\\**. Это место используется для шаблонов, генерируемых командой **Project** > **Export Templates...,** если автоматически **импортировать шаблон в опцию Visual Studio** выбирается в мастере.

Для других (не пользовательских) местоположений необходимо включить файл манифеста (.vstman), который определяет местоположение и другие характеристики шаблона. Файл «Vstman» генерируется вместе с файлом .vstemplate, используемым для шаблонов. Если вы установите расширение с помощью .vsix, вы можете сделать это путем перекомпиляции расширения в Visual Studio 2017. Но если вы используете .msi, вам нужно внести изменения вручную. Список того, что вам нужно сделать, чтобы внести эти изменения, **см. Обновления для расширений, установленных с помощью . MSI** позже на этой странице.

## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Как обновить расширение VSIX с помощью шаблонов проекта или элементов

1. Откройте решение в Visual Studio 2017. Вам будет предложено обновить код. Нажмите кнопку **ОК**.

2. После завершения обновления может потребоваться изменить версию целевого показателя установки. В проекте VSIX откройте файл source.extension.vsixmanifest и выберите вкладку **«Установка целей».** Если поле **Version Range** имеет **14,0 евро,** нажмите **«Изменить»** и измените его, чтобы включить Visual Studio 2017. Например, вы можете установить его на **«14.0,15.0»** для установки расширения либо visual Studio 2015 или Visual Studio 2017, либо до **15,0,** чтобы установить его только на Visual Studio 2017.

3. Перекомпилировать код.

4. Закройте Visual Studio.

5. Установите VSIX.

6. Вы можете протестировать обновление, сделав следующее:

    1. Изменение сканирования файлов активируется следующим ключом реестра:

         **reg добавить hklm-software-microsoft-visualstudio-15.0'VSTemplate /v ОтключитьTemplateScanning /t REG_DWORD /d 1/reg:32**

    2. После того как вы добавили ключ, запустить **devenv /installvstemplates**.

    3. Повторное открытие визуальной студии. Вы должны найти шаблон в ожидаемом месте.

    > [!NOTE]
    > Шаблоны проекта Visual Studio Extensibility недоступны при наличии ключа реестра. Вы должны удалить ключ реестра (и перезапустить **devenv /installvstemplates),** чтобы использовать их.

## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Другие рекомендации по развертыванию шаблонов проекта и элементов

- Избегайте использования файлов шаблонов на молнии. Файлы шаблонов должны быть несжаты, чтобы получить ресурсы и содержимое, поэтому они будут более дорогими в использовании. Вместо этого следует развернуть шаблоны проектов и элементов в качестве отдельных файлов в своем каталоге, чтобы ускорить инициализацию шаблонов. Для расширений VSIX задачи sDK build автоматически распаковывает любой шаблон на молнии при создании файла VSIX.

- Избегайте использования записей package/resource ID для имени шаблона, описания, значка или предварительного просмотра, чтобы избежать ненужных сборочных нагрузок ресурсов во время обнаружения шаблона. Вместо этого можно использовать локализованные манифесты для создания входа шаблона для каждого локали, в котором используются локализованные имена или свойства.

- Если вы включаете шаблоны в качестве элементов файла, генерация манифеста может не дать ожидаемым результатам. В этом случае вам придется добавить манифест с вручную в проект VSIX.

## <a name="file-changes-in-project-and-item-templates"></a>Изменения файлов в шаблонах проекта и элементов
Мы показываем точки различия между Visual Studio 2015 и Visual Studio 2017 версии файлов шаблонов, так что вы можете создать новые файлы правильно.

 Вот файл проекта по умолчанию .vstemplate, созданный Visual Studio 2015:

```xml
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">
  <TemplateData>
    <Name>ProjectTemplate1</Name>
    <Description>ProjectTemplate1</Description>
    <Icon>ProjectTemplate1.ico</Icon>
    <ProjectType>CSharp</ProjectType>
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
    <SortOrder>1000</SortOrder>
    <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>
    <CreateNewFolder>true</CreateNewFolder>
    <DefaultName>ProjectTemplate1</DefaultName>
    <ProvideDefaultName>true</ProvideDefaultName>
  </TemplateData>
  <TemplateContent>
    <Project File="ProjectTemplate.csproj" ReplaceParameters="true">
      <ProjectItem ReplaceParameters="true" TargetFileName="Properties\AssemblyInfo.cs">AssemblyInfo.cs</ProjectItem>
      <ProjectItem ReplaceParameters="true" OpenInEditor="true">Class1.cs</ProjectItem>
    </Project>
  </TemplateContent>
</VSTemplate>

```

 Вот файл .vstman (вы можете найти его в явном каталоге проекта VSIX), который является результатом перестройки проекта VSIX:

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Project">
    <RelativePathOnDisk>CSharp\1033\ProjectTemplate1</RelativePathOnDisk>
    <TemplateFileName>ProjectTemplate1.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>ProjectTemplate1</Name>
        <Description>ProjectTemplate1</Description>
        <Icon>ProjectTemplate1.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <SortOrder>1000</SortOrder>
        <TemplateID>05b79cc9-2146-4716-a8e5-7e085cdd2221</TemplateID>
        <CreateNewFolder>true</CreateNewFolder>
        <DefaultName>ProjectTemplate1</DefaultName>
        <ProvideDefaultName>true</ProvideDefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```

 Информация, предоставляемая элементом [TemplateData,](../extensibility/templatedata-element-visual-studio-templates.md) остается прежней. Элемент VSTemplateContainer>указывает на файл .vstemplate для связанного шаблона. ** \<**

 Вот элемент "по умолчанию vstemplate" файл, созданный Visual Studio 2015:

```xml
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:sdk="http://schemas.microsoft.com/developer/vstemplate-sdkextension/2010">
  <TemplateData>
    <Name>ItemTemplate1</Name>
    <Description>ItemTemplate1</Description>
    <Icon>ItemTemplate1.ico</Icon>
    <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>
    <ProjectType>CSharp</ProjectType>
    <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
    <DefaultName>Class.cs</DefaultName>
  </TemplateData>
  <TemplateContent>
    <References>
      <Reference>
        <Assembly>System</Assembly>
      </Reference>
    </References>
    <ProjectItem ReplaceParameters="true">Class.cs</ProjectItem>
  </TemplateContent>
</VSTemplate>

```

 Вот файл .vstman (вы можете найти его в явном каталоге проекта VSIX), который является результатом перестройки проекта VSIX:

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Item">
    <RelativePathOnDisk>CSharp\1033\ItemTemplate1</RelativePathOnDisk>
    <TemplateFileName>ItemTemplate1.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>ItemTemplate1</Name>
        <Description>ItemTemplate1</Description>
        <Icon>ItemTemplate1.ico</Icon>
        <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
        <DefaultName>Class.cs</DefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>
```

 Информация, предоставляемая элементом ** \<TemplateData>** остается прежней. ** \<Элемент VSTemplateContainer>** указывает на файл .vstemplate для связанного шаблона

 Для получения дополнительной информации о различных элементах файла .vstman, [см.](../extensibility/visual-studio-template-manifest-schema-reference.md)

## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Обновления для расширений, установленных с . Msi

Некоторые расширения на основе MSI развертывают шаблоны в общих местоположениях шаблонов, таких как следующие каталоги:

- **\<Каталог установки Visual Studio>»Common7-IDE\\<ProjectTemplates/ItemTemplates\>**

- **\<Каталог установки Visual Studio>»Common7-IDE-Расширения\\<ExtensionName\> \\<Project/ItemTemplates\>**

Если расширение выполняет развертывание на основе MSI, необходимо создавать манифест шаблона вручную и гарантировать его включение в настройку расширения. Сравните примеры .vstman, перечисленные выше, и [Visual Studio Template Manifest Схема Справка](../extensibility/visual-studio-template-manifest-schema-reference.md).

Создавайте отдельные манифесты для шаблонов проектов и элементов, и они должны указывать на каталог корневого шаблона, как указано выше. Создайте один манифест за расширение и локаль.

## <a name="see-also"></a>См. также

- [Обнаружение шаблона устранения неполадок](troubleshooting-template-discovery.md)
- [Создание пользовательских шаблонов проектов и элементов](creating-custom-project-and-item-templates.md)

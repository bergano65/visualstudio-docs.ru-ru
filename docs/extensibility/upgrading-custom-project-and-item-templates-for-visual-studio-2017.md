---
title: Обновление настраиваемых шаблонов проектов и элементов для Visual Studio 2017
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 39dbe74c8f59171461cca04fc9015782e21fe9da
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/28/2019
ms.locfileid: "66261805"
---
# <a name="upgrade-custom-project-and-item-templates-for-visual-studio-2017"></a>Обновление настраиваемых шаблонов проектов и элементов для Visual Studio 2017

Начиная с Visual Studio 2017, Visual Studio используется для обнаружения шаблонов проектов и элементов, которые были установлены .vsix или MSI-файла по-другому в предыдущих версиях Visual Studio. Если у вас есть расширения, которые используют пользовательский проект или шаблоны элементов, необходимо обновить расширения. В этой статье объясняется, что необходимо сделать.

Это изменение затрагивает только Visual Studio 2017. Он не влияет на предыдущих версиях Visual Studio.

Если вы хотите создать шаблон проекта или элемента как часть расширение VSIX, см. в разделе [Создание настраиваемых шаблонов проектов и элементов](../extensibility/creating-custom-project-and-item-templates.md).

## <a name="template-scanning"></a>Проверка шаблона

В предыдущих версиях Visual Studio **devenv/setup** или **devenv/installvstemplates** проверенных локальный диск, чтобы найти шаблоны проектов и элементов. Начиная с Visual Studio 2017, сканирование выполняется только для местоположения уровня пользователя. Уровень пользователя по умолчанию располагается **%USERPROFILE%\Documents\\< версия Visual Studio\>\Templates\\** . Это расположение используется для шаблонов, созданных **проекта** > **Экспорт шаблонов...**  команды, если **автоматически импортировать шаблон в Visual Studio** выбран в мастере.

Для других расположений (встроенный) необходимо включить файл manifest(.vstman), который указывает расположение и другие характеристики шаблона. А также используется для шаблонов VSTEMPLATE-файл создается vstman-файле. Если установить расширение с помощью .vsix, это можно сделать путем перекомпиляции расширения в Visual Studio 2017. Но если вы используете MSI-файла, необходимо вручную внести изменения. Что необходимо сделать, чтобы эти изменения списка, см. в разделе **обновления для расширения установлены с. MSI** далее на этой странице.

## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Как обновить расширение VSIX с помощью проекта или шаблонов элементов

1. Откройте решение в Visual Studio 2017. Вам будет предложено обновить код. Нажмите кнопку **ОК**.

2. После завершения обновления, может потребоваться изменить версию целевого объекта установки. В проекте VSIX, откройте файл source.extension.vsixmanifest и выберите **цели установки** вкладки. Если **диапазон версий** поле является **[14.0]** , нажмите кнопку **изменить** и измените его для включения Visual Studio 2017. Например, можно разместить его **[14.0,15.0]** установить расширение для Visual Studio 2015 или Visual Studio 2017 или для **[15.0]** для установки в только что Visual Studio 2017.

3. Перекомпилируйте этот код.

4. Закройте Visual Studio.

5. Установите VSIX.

6. Вы можете протестировать обновление следующим образом:

    1. Проверки изменений файлов активируется следующий раздел реестра:

         **REG добавить hklm\software\microsoft\visualstudio\15.0\VSTemplate /v DisableTemplateScanning /t REG_DWORD /d 1 /reg:32**

    2. После добавления ключа, запустите **devenv/installvstemplates**.

    3. Снова откройте Visual Studio. Шаблон необходимо найти в ожидаемом месте.

    > [!NOTE]
    > Шаблоны проектов расширения среды Visual Studio недоступны, если присутствует раздел реестра. Необходимо удалить раздел реестра (и повторно запустите **devenv/installvstemplates**) их использования.

## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Другие рекомендации по развертыванию шаблонов проектов и элементов

- Старайтесь не использовать шаблон в ZIP-файлы. ZIP-файлы должны быть без сжатия, чтобы получить ресурсы и содержимое шаблона, поэтому они будут дороже обходятся для использования. Вместо этого следует развернуть шаблоны проектов и элементов как отдельные файлы в собственном каталоге для ускорения инициализации шаблона. Для расширений VSIX задачи сборки пакета SDK автоматически распакует любой ZIP-шаблон при создании VSIX-файл.

- Избегайте использования операции идентификатор пакета/ресурсов для шаблона имя, описание, значок или при просмотре избежание загрузки сборок ненужных ресурсов во время обнаружения шаблонов. Вместо этого можно использовать локализованную манифесты для создания шаблона записи для каждого языкового стандарта, которая использует локализованные имена или свойства.

- Если вы включаете шаблоны как элементы файла, создания манифеста вы не получите ожидаемых результатов. В этом случае необходимо добавить в проект VSIX вручную создать манифест.

## <a name="file-changes-in-project-and-item-templates"></a>Изменения файлов в шаблоны проектов и элементов
Мы покажем точки разницу между Visual Studio 2015 и Visual Studio 2017 версий файлов шаблонов, которые можно создавать новые файлы правильно.

 Вот VSTEMPLATE-файл проекта по умолчанию, созданные Visual Studio 2015:

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

 Ниже приведен vstman-файле (его можно найти в каталоге манифеста проекта VSIX), полученное в результате перестроения проекта VSIX.

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

 Сведения, предоставляемые [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) элемент остается неизменным.  **\<VSTemplateContainer >** элемент указывает на файл VSTEMPLATE для связанного шаблона.

 Ниже приведен VSTEMPLATE-файл элемента по умолчанию, созданные Visual Studio 2015.

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

 Ниже приведен vstman-файле (его можно найти в каталоге манифеста проекта VSIX), полученное в результате перестроения проекта VSIX.

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

 Сведения, предоставляемые  **\<TemplateData >** элемент остается неизменным.  **\<VSTemplateContainer >** элемент указывает на файл VSTEMPLATE для связанного шаблона

 Дополнительные сведения о различных элементов vstman-файле, см. в разделе [Visual Studio шаблон манифеста Справочник по схеме](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Установленные обновления для расширений с. MSI

Некоторые расширения на основе MSI развертывать шаблоны для общих расположений шаблона, такие как следующие каталоги:

- **\<Каталог установки Visual Studio > \Common7\IDE\\< Шаблоны_проекта/ItemTemplates >**

- **\<Каталог установки Visual Studio > \Common7\IDE\Extensions\\< ExtensionName\>\\< проект/ItemTemplates >**

Если расширение выполняет развертывание на основе MSI, необходимо вручную создать манифест шаблона и убедитесь, что он включен в установку расширения. В приведенных выше примерах .vstman сравнения и [Visual Studio шаблон манифеста Справочник по схеме](../extensibility/visual-studio-template-manifest-schema-reference.md).

Создайте отдельный манифесты для шаблонов проектов и элементов, и они должны указывать на корневой каталог шаблонов как указано выше. Создайте один манифест каждого расширения и языковой стандарт.

## <a name="see-also"></a>См. также

- [Устранение неполадок обнаружения шаблонов](troubleshooting-template-discovery.md)
- [Создание пользовательских шаблонов проектов и элементов](creating-custom-project-and-item-templates.md)

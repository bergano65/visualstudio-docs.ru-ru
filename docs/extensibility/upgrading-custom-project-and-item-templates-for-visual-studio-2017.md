---
title: Обновление пользовательских шаблонов проектов и элементов для Visual Studio 2017 г. | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: af60281e7211e7b16e86200c02aef791d26da274
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31143482"
---
# <a name="upgrading-custom-project-and-item-templates-for-visual-studio-2017"></a>Обновление пользовательских шаблонов проектов и элементов для Visual Studio 2017 г.

Начиная с Visual Studio 2017 г., Visual Studio обнаруживает шаблоны проектов и элементов, которые были установлены .vsix или MSI-файла в предыдущих версиях Visual Studio различными способами. Если вы владеете, использующих пользовательский проект или шаблоны элементов расширения, необходимо обновить расширения. В этом разделе объясняется, что необходимо сделать.

Это изменение затрагивает только Visual Studio 2017 г. Он не влияет на предыдущих версиях Visual Studio.

Если вы хотите создать шаблон проекта или элемента в рамках расширение VSIX, см. раздел [Создание пользовательские шаблоны проектов и элементов](../extensibility/creating-custom-project-and-item-templates.md).

## <a name="template-scanning"></a>Проверка шаблона

В предыдущих версиях Visual Studio **devenv/setup** или **devenv/installvstemplates** проверенных локальный диск для поиска шаблонов проектов и элементов. Начиная с Visual Studio 2017 г., сканирование выполняется только для местоположения уровня пользователя. По умолчанию уровень пользователя находится в **%USERPROFILE%\Documents\\< версия Visual Studio\>\Templates\\**. Это расположение используется для шаблонов, созданных **проекта** > **Экспорт шаблонов...**  команды, если **автоматически импортировать шаблон в Visual Studio** в мастере выбран параметр.

Для других источников (отличных от пользователя) необходимо включить файл manifest(.vstman), который указывает расположение и другие характеристики шаблона. А также используется для шаблонов VSTEMPLATE-файл будет создан файл .vstman. Если установить расширения с помощью .vsix, это можно сделать путем повторной компиляции модуля в Visual Studio 2017 г. Но если вы используете MSI-файла, необходимо вручную внести изменения. Список, что нужно сделать, чтобы эти изменения, см. **обновления установлены расширения с. MSI** далее в этом разделе.  
  
## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Как обновить расширение VSIX с проектом или шаблоны элементов  

1.  Откройте решение в Visual Studio 2017 г. Вам будет предложено обновить код. Нажмите кнопку **ОК**.  
  
2.  После завершения обновления, может потребоваться изменить версию целевой объект установки. В проект VSIX, откройте файл source.extension.vsixmanifest и выберите **цели установки** вкладки. Если **диапазон версий** поле является **[14.0]**, нажмите кнопку **изменить** и измените его, чтобы включить Visual Studio 2017 г. Например, можно присвоить его **[14.0,15.0]** для установки расширения для Visual Studio 2015 или Visual Studio 2017 г. или для **[15.0]** для ее установки только Visual Studio 2017 г.  
  
3.  Перекомпилируйте код.  
  
4.  Закройте Visual Studio.  
  
5.  Установите VSIX.  
  
6.  Обновления можно проверить следующим образом:  
  
    1.  Проверки изменений файлов активируется в следующий раздел реестра:  
  
         **REG добавить hklm\software\microsoft\visualstudio\15.0\VSTemplate /v DisableTemplateScanning /t REG_DWORD /d 1 /reg:32**  
  
    2.  После добавления ключа запуска **devenv/installvstemplates**.  
  
    3.  Снова откройте Visual Studio. Шаблон должен находиться в ожидаемом расположении.  
  
    > [!NOTE]
    >  Шаблоны проектов расширения среды Visual Studio недоступны, если раздел реестра присутствует. Необходимо удалить раздел реестра (и повторно запустите **devenv/installvstemplates**) их использования.  
  
## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Другие рекомендации по развертыванию шаблонов проектов и элементов  
  
-   Старайтесь не использовать шаблон ZIP-файлов. ZIP-файлы должны быть без сжатия, чтобы получить ресурсы и содержимое шаблона, поэтому они будут costlier для использования. Вместо этого следует развернуть шаблонов проектов и элементов как отдельные файлы в каталоге, свои собственные для ускорения инициализации шаблона. Для расширений VSIX задачи сборки пакета SDK автоматически Распакуйте любой сжатый шаблон при создании VSIX-файл.  
  
-   Избегайте использования во избежание ненужных ресурсов загрузки сборок во время обнаружения шаблона записи идентификатор пакета или ресурсов для шаблона имя, описание, значок или предварительного просмотра. Вместо этого можно использовать для создания шаблона записи для каждого языкового стандарта, который использует локализованные имена, свойства или локализованные манифесты.  
  
-   При включении шаблоны в качестве элемента файла создания манифеста может не предоставить ожидаемых результатов. В этом случае необходимо добавить в проект VSIX вручную созданный манифест.  
  
## <a name="file-changes-in-project-and-item-templates"></a>Изменения файла в шаблоны проектов и элементов  
Мы отображение точек разницы между Visual Studio 2015 и Visual Studio 2017 г версиями файлов шаблона, можно создать новые файлы правильно.  
  
 Вот VSTEMPLATE-файл проекта по умолчанию, созданные Visual Studio 2015.  
  
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
  
 Ниже приведен файл .vstman (его можно найти в каталоге манифеста VSIX проекта), является результатом перестроения проекта VSIX.  
  
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
  
 Сведения, предоставляемые [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) элемент остается неизменным.  **\<VSTemplateContainer >** элемент указывает на файл VSTEMPLATE связанный шаблон.  
  
 Вот VSTEMPLATE-файл элемента по умолчанию, созданные Visual Studio 2015.  
  
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
  
 Ниже приведен файл .vstman (его можно найти в каталоге манифеста VSIX проекта), является результатом перестроения проекта VSIX.  
  
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
  
 Сведения, предоставляемые  **\<TemplateData >** элемент остается неизменным.  **\<VSTemplateContainer >** элемент указывает на файл VSTEMPLATE связанный шаблон  
  
 Дополнительные сведения о различных элементах .vstman файла см. в разделе [Visual Studio манифеста Справочник по схеме шаблонов](../extensibility/visual-studio-template-manifest-schema-reference.md).  
  
## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Установленные обновления для расширений с. MSI-ФАЙЛ

Некоторые расширения на основе MSI развертывания шаблонов стандартных расположениях шаблона из следующего:

- **\<Каталог установки Visual Studio > \Common7\IDE\\< Шаблоны_проекта/элементов >**

- **\<Каталог установки Visual Studio > \Common7\IDE\Extensions\\< ExtensionName\>\\< проектов и элементов >**

Если модуль выполняет развертывание на основе MSI, необходимо вручную создать манифест шаблона и убедитесь, что он включен в установку расширения. Сравнение приведенные выше примеры .vstman и [Visual Studio манифеста Справочник по схеме шаблонов](../extensibility/visual-studio-template-manifest-schema-reference.md).

Необходимо создать отдельный манифесты для шаблонов проектов и элементов, и они должны указывать на корневой каталог шаблонов как указано выше. Создайте один манифест в модуль и языковой стандарт.

## <a name="see-also"></a>См. также

[Устранение неполадок обнаружения шаблона](troubleshooting-template-discovery.md)  
[Создание пользовательских шаблонов проектов и элементов](creating-custom-project-and-item-templates.md)
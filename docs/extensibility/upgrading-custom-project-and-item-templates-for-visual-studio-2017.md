---
title: "Обновление пользовательские шаблоны проектов и элементов для Visual Studio «15» | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad02477b-e101-4f32-aeb7-292bf95d5c2f
caps.latest.revision: 3
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 512014c5070e4314ad2b7d0e8c5c404c43f32cd9
ms.openlocfilehash: af2000e6c3649b625c54ed9dc2706d64642016ad
ms.lasthandoff: 02/22/2017

---
# <a name="upgrading-custom-project-and-item-templates-for-visual-studio-2017"></a>Обновление пользовательских шаблонов проектов и элементов для Visual Studio 2017 г.
Начиная с Visual Studio 2017 г., Visual Studio изменяет способ обнаружения шаблонов проектов и элементов, которые были установлены с .vsix или MSI-файл. Если у вас есть расширения, использующих пользовательский проект или шаблоны элементов, необходимо обновить расширения. В этом разделе объясняется, что необходимо сделать.  
  
 Это изменение затрагивает только Visual Studio 2017 г.. Он не влияет на предыдущие версии Visual Studio.  
  
 Если требуется создать шаблон проекта или элемента в рамках расширения VSIX, см. раздел [Создание пользовательские шаблоны проектов и элементов](../extensibility/creating-custom-project-and-item-templates.md).  
  
## <a name="template-scanning"></a>Проверка шаблона  
 Ранее **devenv/setup** или **devenv /installvstemplates** сканирование локальный диск для поиска шаблонов проектов и элементов. Начиная с предварительной версии 4, сканирование будет выполняться только для уровня пользователя расположение (**%USERPROFILE%\Documents\\<Visual studio=""></Visual>\>экспортировать шаблоны \My\\**), используемый для шаблонов, созданных **файл и экспорт шаблонов** команды.  
  
 Для других источников (отличных от пользователя) необходимо включить файл manifest(.vstman), который указывает расположение и другие характеристики шаблона. Файл .vstman, созданный вместе с VSTEMPLATE-файл используется для шаблонов. Если установить расширение с помощью .vsix, это можно сделать путем повторной компиляции модуля в Visual Studio 2017 г. Но если использовать MSI-файл, необходимо внести изменения вручную. Список то, что нужно сделать, чтобы эти изменения, в разделе **обновления для установки расширения с. MSI** далее в этом разделе.  
  
## <a name="how-to-update-a-vsix-extension-with-project-or-item-templates"></a>Обновление расширения VSIX с проектом или шаблонов элементов  
 Эта процедура объясняет, как для Visual Studio 2017 г.
1.  Откройте решение в Visual Studio 2017 г. Вам будет предложено обновить код. Нажмите кнопку **ОК**.  
  
2.  После завершения обновления, может потребоваться изменить версию целевой объект установки. В проект VSIX, откройте файл source.extension.vsixmanifest и выберите **цели установки** вкладки. Если **диапазон версий** поле является **[14.0]**, нажмите кнопку **изменить** и изменить его для включения Visual Studio 2017 г. Например, можно присвоить его **[14.0,15.0]** для установки расширения для Visual Studio 2015 или Visual Studio 2017 г. или для **[15,0]** установить его просто Visual Studio 2017 г..  
  
3.  Перекомпилируйте код.  
  
4.  Закройте Visual Studio.  
  
5.  Установите VSIX.  
  
6.  Обновления можно проверить следующим образом:  
  
    1.  Проверки изменений файлов активируется следующий раздел реестра:  
  
         **REG добавить hklm\software\microsoft\visualstudio\15.0\VSTemplate /v DisableTemplateScanning /t REG_DWORD /d 1 /reg:32**  
  
    2.  После добавления ключа запуска **devenv /installvstemplates**.  
  
    3.  Снова откройте Visual Studio. Шаблон должен находиться в другом месте.  
  
    > [!NOTE]
    >  Шаблоны проектов расширяемости Visual Studio недоступны, если присутствует раздел реестра. Необходимо удалить раздел реестра (и повторно **devenv /installvstemplates**) для их использования.  
  
## <a name="other-recommendations-for-deploying-project-and-item-templates"></a>Другие рекомендации по развертыванию шаблонов проектов и элементов  
  
-   Старайтесь не использовать шаблон ZIP-файлов. ZIP-шаблон необходимые файлы без сжатия, чтобы получить ресурсы и сведения, поэтому они будут costlier для использования. Вместо этого следует развернуть шаблоны проектов и элементов как отдельные файлы в свой собственный каталог для ускорения инициализации шаблонов. Для расширений VSIX задач построения SDK автоматически распакуйте ZIP-шаблонах во время создания файла VSIX.  
  
-   Избегайте использования операции идентификатор пакета и ресурсов по имени шаблона, описание, значок или предварительного просмотра, чтобы избежать излишнего сборка загружается во время обнаружения шаблона. Вместо этого можно использовать локализованные манифесты для создания шаблона записи для каждого языкового стандарта, который использует локализованные имена или свойства.  
  
-   При включении шаблоны в качестве элемента файла создания манифеста может не предоставить ожидаемых результатов. В этом случае необходимо добавить манифест вручную создан проектом VSIX.  
  
## <a name="file-changes-in-project-and-item-templates"></a>Изменения файла в проект и шаблоны элементов  
 Мы покажем точки различие между версией Visual Studio 2015 и версия Visual Studio «15» файлов шаблонов, чтобы можно было создать новые файлы правильно.  
  
 Ниже приведен файл с расширением VSTEMPLATE проекта по умолчанию, созданные Visual Studio 2015:  
  
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
  
 Это файл .vstman (его можно найти в каталоге манифеста проекта VSIX), полученным в результате повторного построения проекта VSIX:  
  
```  
VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
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
  
 Сведения, предоставляемые [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) элемент остается прежним. ** \<VSTemplateContainer настроек** элемент указывает на файл VSTEMPLATE связанный шаблон.  
  
 Ниже приведен файл с расширением VSTEMPLATE элемента по умолчанию, созданные Visual Studio 2015:  
  
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
  
 Это файл .vstman (его можно найти в каталоге манифеста проекта VSIX), полученным в результате повторного построения проекта VSIX:  
  
```  
VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
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
  
 Сведения, предоставляемые ** \<TemplateData настроек** элемент остается прежним. ** \<VSTemplateContainer настроек** элемент указывает VSTEMPLATE-файлу для связанного шаблона  
  
 Дополнительные сведения о различных элементах файла .vstman в разделе [Visual Studio манифеста Справочник по схеме шаблонов](../extensibility/visual-studio-template-manifest-schema-reference.md).  
  
## <a name="upgrades-for-extensions-installed-with-an-msi"></a>Установленные обновления для расширения с. MSI  
 Некоторые расширения на основе MSI развернуть шаблоны в стандартные расположения шаблона из следующего:  
  
-   **\<Каталог установки Visual Studio настроек \Common7\IDE\\<ProjectTemplates temtemplates="">**</ProjectTemplates>  
  
-   **\<Каталог установки Visual Studio настроек \Common7\IDE\Extensions\\<>\>\\<Project temtemplates="">**</Project>  
  
 Модуль выполняет развертывание на основе MSI, необходимо вручную создать манифест шаблона и убедитесь, что он включен в установку расширения. Следует сравнить приведенные выше примеры .vstman и [Visual Studio манифеста Справочник по схеме шаблонов](../extensibility/visual-studio-template-manifest-schema-reference.md). Чтобы увидеть, что необходимо включить  
  
 Необходимо создать отдельный манифесты для шаблонов проектов и элементов, и они должны указывать на корневой каталог шаблонов как указано выше. Необходимо создать один манифест на расширение и языкового стандарта.  
  
## <a name="troubleshooting-template-installation"></a>Устранение неполадок при установке шаблона  
 При возникновении проблем с развертыванием шаблонов проекта или элемента, можно включить ведение журналов диагностики.  
  
1.  Выполните следующую команду, чтобы задать раздел реестра для включения ведения журнала:  
  
     **REG добавить HKCU\software\microsoft\visualstudio\15.0_Config\VSTemplate /v EnableTemplateDiscoveryLog /t REG_DWORD /d 1**  
  
2.  Запуска Visual Studio и откройте новый проект и новый элемент диалоговые окна для инициализации деревьев оба шаблона. Журнал Шаблон появится в **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0\VsTemplateDiagnosticsList.csv**. Каждый шаблон дерева инициализации добавляет записи в этот журнал.  
  
 Файл журнала содержит следующие столбцы:  
  
-   **FullPathToTemplate**, который имеет следующие значения:  
  
    -   1 для развертывания на основе манифеста  
  
    -   0 для развертывания на диске  
  
-   **TemplateFileName**  
  
-   Другие свойства шаблона

---
title: Визуальный шаблон студии Манифест Схема Ссылка (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dbe46851d9df85569be796b4147217bd7db450ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697988"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Визуальный шаблон студии манифест схемы ссылки
Эта схема описывает формат манифеста шаблона Visual Studio *(.vstman*) файлов, которые генерируются для проектов Visual Studio или шаблонов элементов. Схема также описывает местоположение и другую соответствующую информацию о шаблоне.

 : Поскольку существуют отдельные каталоги шаблонов элементов и проектов, манифест никогда не должен иметь сочетание шаблонов элементов и проектов.

> [!IMPORTANT]
> Этот манифест доступен начиная с Visual Studio 2017.

## <a name="vstemplatemanifest-element"></a>Элемент VSTemplateManifest
 Корневой элемент манифеста.

### <a name="attributes"></a>Атрибуты

- **Версия**: Строка, представляющая версию манифеста шаблона. Обязательный элемент.

- **Логово**: Строка, представляющая локал из шаблонов или локализующих стихов манифеста шаблона. Значение локализации применяется ко всем шаблонам. Для каждого места. Необязательный параметр.

### <a name="child-elements"></a>Дочерние элементы

- **VSTemplateContainer** Дополнительные.

- **VSTemplateDir** Дополнительные.

### <a name="parent-element"></a>Родительский элемент
 Нет.

## <a name="vstemplatecontainer"></a>VSTemplateContainer
 Контейнер шаблона проявляется элементами. Манифест имеет один контейнер шаблона для каждого шаблона, который он определяет.

### <a name="attributes"></a>Атрибуты
 **VSTemplateType**: Значение строки, которое определяет тип`"Project"` `"Item"`шаблона `"ProjectGroup"`( , или ). Обязательно

### <a name="child-elements"></a>Дочерние элементы

- **RelativePathOnDisk**: Относительный путь файла шаблона на диске. Это место также определяет размещение шаблона в дереве шаблонов, отображаемом в диалоге **New Project** или **New Item.** Для шаблонов, развернутых в виде каталога и отдельных файлов, этот путь относится к каталогу, содержащему файлы шаблонов. Для шаблонов, развернутых в виде файла *.zip,* этот путь должен быть путем к файлу *.zip.*

- Элемент TemplateHeadHeader: Элемент [TemplateData,](../extensibility/templatedata-element-visual-studio-templates.md) описывающий заголовок.

### <a name="parent-element"></a>Родительский элемент
 **VSTemplateManifest**

## <a name="vstemplatedir"></a>VSTemplateDir
 Описывает каталог, в котором находится шаблон. Манифест может содержать несколько записей **VSTemplateDir,** чтобы предоставить локализованное имя и сортировать заказ для каталогов, чтобы контролировать их появление в дереве категории шаблонов.

 Из-за их дизайна записи **VSTemplateDir** должны отображаться только в нелокальных манифестах.

### <a name="attributes"></a>Атрибуты
 Нет.

### <a name="child-elements"></a>Дочерние элементы

- **RelativePath**: Путь шаблона. Там может быть только один вход на путь, так что первый победит для всех манифестов.

- **Локализованноеимя**: Элемент **NameDescriptionIcon,** который определяет локализованное имя. Необязательный параметр.

- **SortOrder**: Строка, которая определяет порядок сортировки. Необязательный параметр.

- **ParentFolderOverrideName**: Переопределенное имя родительской папки. Необязательный параметр. Этот элемент имеет атрибут **имени,** который представляет собой значение строки, опознавававшее имя.

### <a name="parent-element"></a>Родительский элемент
 **VSTemplateManifest**

## <a name="namedescriptionicon"></a>ИмяОписаниеИкон
 Определяет имя и описание, возможно, для локализованных шаблонов. Смотрите **LocalizedName** выше.

### <a name="attributes"></a>Атрибуты

- **Пакет**: Значение строки, которое определяет пакет. Необязательный параметр.

- **Идентификатор**: Значение строки, опознавававав идентификатор. Необязательный параметр.

### <a name="child-elements"></a>Дочерние элементы
 Нет.

### <a name="parent-element"></a>Родительский элемент
 **ЛокализованоИмя**

## <a name="examples"></a>Примеры
 Следующий код является примером шаблона проекта *.vstman* файл.

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
  <VSTemplateContainer TemplateType="Project">
    <RelativePathOnDisk>CSharp\1033\TestProjectTemplate</RelativePathOnDisk>
    <TemplateFileName>TestProjectTemplate.vstemplate</TemplateFileName>
    <VSTemplateHeader>
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
        <Name>TestProjectTemplate</Name>
        <Description>TestProjectTemplate</Description>
        <Icon>TestProjectTemplate.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>
        <SortOrder>1000</SortOrder>
        <TemplateID>aac0aeea-7883-4003-992f-937d53d70ab1</TemplateID>
        <CreateNewFolder>true</CreateNewFolder>
        <DefaultName>TestProjectTemplate</DefaultName>
        <ProvideDefaultName>true</ProvideDefaultName>
      </TemplateData>
    </VSTemplateHeader>
  </VSTemplateContainer>
</VSTemplateManifest>

```

 Следующий код является примером шаблона элемента *.vstman* файла.

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

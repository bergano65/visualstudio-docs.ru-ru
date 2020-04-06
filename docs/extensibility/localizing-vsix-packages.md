---
title: Локализация пакетов VSIX Документы Майкрософт
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7d2d4222e45d56447951e86d558af9983a0d1cc9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702902"
---
# <a name="localizing-vsix-packages"></a>Локализация пакетов VSIX

Вы можете локализовать пакет VSIX, создав файл *Extension.vsixlangpack* для каждого целевого языка, а затем поместить их в правильную папку. При установке локализованного пакета локализованное название расширения отображается вместе с локализованным описанием. Если вы предоставите локализованный файл лицензии или URL-адрес, указывают на локализованную информацию, они также отображаются.

Если содержимое пакета VSIX содержит VSPackage, который добавляет команды меню или другой uI, см. [Команды меню Localize](../extensibility/localizing-menu-commands.md) для получения информации о локализации новых элементов uI.

## <a name="directory-structure"></a>Структура каталогов

 Когда пользователь устанавливает расширение, **расширения и обновления** проверяют верхний уровень пакета VSIX для папки, имя которой совпадает с локалью Visual Studio целевого компьютера. Если **extensions and Updates** находит файл *.vsixlangpack* в папке, он заменяет локализованные значения в этом файле на соответствующие значения в файле *.vsixmanifest.* Эти значения отображаются при установке расширения. Ниже приводится структура каталога для пакета VSIX, локализованного на испанском (es-ES) и французском (fr-FR).

```text
.
├── MyExtension.dll
├── Extension.vsixmanifest
├── [Content_Types].xml
├── es-ES
│   └── Extension.vsixlangpack
└── fr-FR
    └── Extension.vsixlangpack
```

> [!NOTE]
> Поддерживаемые VSIX шаблоны проекта [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] в манифесте VSIX и назовите его *source.extension.vsixmanifest*. Когда Visual Studio создает проект, она копирует содержимое этого файла в Extension.VsixManifest в пакете VSIX.

## <a name="the-extensionvsixlangpack-file"></a>Файл Extension.vsixlangpack

Файл *Extension.vsixlangpack* следует [схеме VSIX Language Pack 2.0](../extensibility/vsix-language-pack-schema-2-0-reference.md). Эта схема `PackageLanguagePackManifest`имеет, который сразу же `Metadata` сопровождается элементом ребенка. Элемент Metadata может содержать до 6 `DisplayName` `Description`элементов `License` `ReleaseNotes`ребенка, , `Icon` `MoreInfo`, , и . Эти элементы ребенка `Description` `MoreInfo`соответствуют `ReleaseNotes` `DisplayName`, `Icon` , , `Metadata` `License`, , , и элементы ребенка *элемента Extension.vsixmanifest* файла.

При создании файла vsixlangpack необходимо `Include in Vsix` настроить `true`свойство. В противном случае локальный текст установки будет проигнорирован.

### <a name="to-set-the-include-in-vsix-property"></a>Установить включение в свойство Vsix

1. В **Solution Explorer**, правой кнопкой мыши Extension.vsixlangpack файл, а затем нажмите **Свойства**.

2. В **сетке свойств**, нажмите Включить в `true` **Vsix**, и установить его значение.

## <a name="example"></a>Пример

### <a name="description"></a>Описание

В следующем примере показаны соответствующие части файла *Extension.vsixmanifest.* Файл также включает в себя соответствующий файл *Extension.vsixlangpack* для испанского языка. Значения из языкового пакета заменяют значения из манифеста, если язык Visual Studio целевого компьютера установлен на испанский язык.

### <a name="code"></a>Код

- -*Extension.vsixmanifest*

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageManifest ...>
  <Metadata ...>
    <DisplayName>Family Tree</DisplayName>
    <Description>This extension places a custom treeview control in the toolbox that is optimized for handling family tree information.</Description>
    <MoreInfo>http://www.contoso.com/products/FamilyTree.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
  <Installation .../>
  <Dependencies .../>
  <Prerequisites .../>
  <Assets .../>
</PackageManifest>
```

- -*Extension.vsixlangpack*

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageLanguagePackManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <DisplayName>Arbol de Familia</DisplayName>
    <Description> Esta extensión pone control personalizado en la caja de herramientas por manejar información de familia.</Description>
    <MoreInfo> http://www.contoso.com/products/es/ArbolDeFamilia.htm</MoreInfo>
    <License>Eula.rtf</License>
    <ReleaseNotes>ReleaseNotes.rtf</ReleaseNotes>
    <Icon>Icon.png</Icon>
  </Metadata>
</PackageLanguagePackManifest>
```

## <a name="see-also"></a>См. также

|Заголовок|Описание|
|-----------|-----------------|
|[Схема языкового пакета VSIX 2.0](vsix-language-pack-schema-2-0-reference.md)|Пакет языков VSIX описывает информацию о локализации файла развертывания .vsix.|
|[Анатомия пакета VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Описывает структуру и содержимое пакета vsix.|
|[Локализация команд меню](../extensibility/localizing-menu-commands.md)|Показывает, как локализовать другие текстовые ресурсы в расширении.|

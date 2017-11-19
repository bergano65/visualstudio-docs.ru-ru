---
title: "Локализация пакетов VSIX | Документы Microsoft"
ms.custom: 
ms.date: 10/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
caps.latest.revision: "13"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6a8bb9332b30e5dbc410bdacea3800713b25b10f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="localizing-vsix-packages"></a>Локализация пакетов VSIX

Для локализации пакета VSIX можно создать файл Extension.vsixlangpack для каждого требуемого языка и поместить эти файлы в папке. При установке локализованного пакета вместе с локализованное описание отображается локализованное имя расширения. Если указать локализованный файл лицензии или URL-адрес, указывающий на локализованные сведения, они также отображаются.

Если содержимое пакета VSIX включает пакет VSPackage, который добавляет команды меню или другой пользовательский Интерфейс. в разделе [локализация команды меню](../extensibility/localizing-menu-commands.md) сведения о локализации новые элементы пользовательского интерфейса.

## <a name="directory-structure"></a>Структура каталогов

 Когда пользователь устанавливает расширение, **расширения и обновления** проверяет верхний уровень пакета VSIX для папки, имя которого соответствует языку Visual Studio на целевом компьютере. Если **расширения и обновления** находит a .vsixlangpack файлов в папке, он подставляет локализованные значения из данного файла в файле VSIXMANIFEST соответствующие значения. Эти значения отображаются при установке расширения. Следующий пример показывает структуру папок для пакета VSIX, который локализован на испанский (es-ES) и французского (fr-FR).  

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
> Шаблоны проекта VSIX поддерживается в [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] создания манифеста VSIX и назовите его source.extension.vsixmanifest. Когда Visual Studio создает проект, он копирует содержимое этого файла в файл Extension.VsixManifest в пакет VSIX.

## <a name="the-extensionvsixlangpack-file"></a>Файл Extension.vsixlangpack

Имена файлов Extension.vsixlangpack [VSIX Language Pack схемы 2.0](../extensibility/vsix-language-pack-schema-2-0-reference.md). Эта схема имеет `PackageLanguagePackManifest`, которая непосредственно следует `Metadata` дочерний элемент. Элемент метаданных может содержать до 6 дочерние элементы, `DisplayName`, `Description`, `MoreInfo`, `License`, `ReleaseNotes`, и `Icon`. Эти дочерние элементы соответствуют `DisplayName`, `Description`, `MoreInfo`, `License`, `ReleaseNotes`, и `Icon` дочерних элементов `Metadata` элемент файл Extension.vsixmanifest.

При создании файла vsixlangpack необходимо задать `Include in Vsix` свойства `true`. В противном случае текст локализованного установочного будет пропущен.

### <a name="to-set-the-include-in-vsix-property"></a>Установка включить в Vsix-свойство

1. В **обозревателе решений**, щелкните правой кнопкой мыши файл Extension.vsixlangpack и нажмите кнопку **свойства**.

2.  В сетке свойств нажмите кнопку **включить в Vsix**и присвойте ему значение `true`.

## <a name="example"></a>Пример

### <a name="description"></a>Описание

В следующем примере показано соответствующих частей файл Extension.vsixmanifest, а также соответствующий файл Extension.vsixlangpack для испанского языка. Значения из языкового пакета заменяют значения из манифеста, если языковой стандарт Visual Studio на целевом компьютере установлен испанский.

### <a name="code"></a>Код

 [Extension.vsixmanifest]

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

 [Extension.vsixlangpack]

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
|[Справочник по схеме LanguagePack 2.0 VSIX](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Языковой пакет VSIX описывает сведения о локализации файла развертывания с расширением VSIX.|
|[Составляющие пакета VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Описывает структуру и содержимое пакета vsix.|
|[Локализация команд меню](../extensibility/localizing-menu-commands.md)|Показан способ локализации ресурсов других текста в расширении.|
---
title: Локализация пакетов VSIX | Документация Майкрософт
ms.custom: ''
ms.date: 10/26/2017
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- localize package
- localize extension
- localized deployment
ms.assetid: 10e80b13-b39e-466c-a7c8-774a862355af
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 85d32f25e8dd1f2f56af0857f2be0ff24c4d3126
ms.sourcegitcommit: 159ed9d4f56cdc1dff2fd19d9dffafe77e46cd4e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/21/2018
ms.locfileid: "53740251"
---
# <a name="localizing-vsix-packages"></a>Локализация пакетов VSIX

Вы можете локализовать пакета VSIX, создав *Extension.vsixlangpack* файл для каждого целевого языка и поместить эти файлы в папке. При установке локализованного пакета локализованное описание отобразите локализованное имя расширения. Если вы указали локализованный файл лицензии или URL-адрес, указывающий на локализованные сведения, они также отображаются.

Если содержимое пакета VSIX включает пакет VSPackage, который добавляет команды меню или другой пользовательский Интерфейс, см. в разделе [локализация команд меню](../extensibility/localizing-menu-commands.md) сведения о локализации новых элементов пользовательского интерфейса.

## <a name="directory-structure"></a>Структура каталогов

 Когда пользователь устанавливает расширение, **расширения и обновления** проверяет верхний уровень пакета VSIX для папки, имя которого соответствует языку Visual Studio конечного компьютера. Если **расширения и обновления** находит *.vsixlangpack* файл в папке, он подставляет локализованные значения в соответствующие значения в этом файле *.vsixmanifest*файл. Эти значения отображаются при установке расширения. В следующем примере структуру каталогов для пакета VSIX, который локализован на испанский (es-ES) и французского (fr-FR).  

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
> Шаблоны проектов VSIX поддерживается в [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] создать манифест VSIX и назовите его *source.extension.vsixmanifest*. Когда Visual Studio создает проект, он копирует содержимое этого файла в Extension.VsixManifest в пакете VSIX.

## <a name="the-extensionvsixlangpack-file"></a>Файл Extension.vsixlangpack

*Extension.vsixlangpack* файл следующим [схема языкового пакета VSIX 2.0](../extensibility/vsix-language-pack-schema-2-0-reference.md). Эта схема имеет `PackageLanguagePackManifest`, которая непосредственно следует `Metadata` дочерний элемент. Элемент метаданных может содержать до 6 дочерних элементов, `DisplayName`, `Description`, `MoreInfo`, `License`, `ReleaseNotes`, и `Icon`. Эти дочерние элементы соответствуют `DisplayName`, `Description`, `MoreInfo`, `License`, `ReleaseNotes`, и `Icon` дочерними элементами элемента `Metadata` элемент *Extension.vsixmanifest*файл.

При создании файла vsixlangpack, необходимо задать `Include in Vsix` свойства `true`. В противном случае текст локализованного установочного будет игнорироваться.

### <a name="to-set-the-include-in-vsix-property"></a>Чтобы задать включают свойства Vsix

1. В **обозревателе решений**, щелкните правой кнопкой мыши файл Extension.vsixlangpack и нажмите кнопку **свойства**.

2.  В **сетки свойств**, нажмите кнопку **включить в Vsix**и присвойте ему значение `true`.

## <a name="example"></a>Пример

### <a name="description"></a>Описание:

В следующем примере показано нужные части *Extension.vsixmanifest* файла. В этом файле содержится соответствующий *Extension.vsixlangpack* файл для испанского языка. Значения из языкового пакета замените значения из манифеста, если задано значение испанский языковой стандарт Visual Studio для конечного компьютера.

### <a name="code"></a>Код

 [*Extension.vsixmanifest*]

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

 [*Extension.vsixlangpack*]

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

|Заголовок|Описание:|
|-----------|-----------------|
|[Справочник по схеме 2.0 языкового пакета VSIX](/visualstudio/extensibility/vsix-language-pack-schema-2-0-reference)|Языковой пакет VSIX описывает информацию локализации VSIX-файл развертывания.|
|[Составляющие пакета VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Описывает структуру и содержимое пакета vsix.|
|[Локализация команд меню](../extensibility/localizing-menu-commands.md)|Показано, как локализовать ресурсы текста в расширении.|
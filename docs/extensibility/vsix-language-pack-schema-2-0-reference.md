---
title: Справочник по схеме языкового пакета VSIX 2,0 | Документация Майкрософт
ms.date: 10/26/2017
ms.topic: conceptual
helpviewer_keywords:
- language pack
- localize vsix
- localize package
- localize extension
ms.assetid: 2a2932bc-cdbe-4d32-91fa-a3e0474f9098
ms.author: zorio
author: zoeyr
manager: jillfra
ms.openlocfilehash: f97fd5aee27cdc97cf6eb5731da9fad9cb999e18
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "78169343"
---
# <a name="vsix-language-pack-schema-20-reference"></a>Справочник по схеме языкового пакета VSIX 2,0

Схема языкового пакета VSIX предоставляет локализованные сведения об установке для пакетов VSIX. Версия 2,0 этой схемы поддерживает дополнительные элементы локализации.

## <a name="language-pack-schema"></a>Схема языкового пакета

Корневой элемент файла языкового пакета имеет `<PackageLanguagePackManifest>` атрибут `Version` , являющийся версией формата языкового пакета. В этой статье описывается версия 2,0 языка языкового пакета, который указывается в манифесте путем присвоения `Version` атрибуту значения `Version="2.0.0"` . Корневой элемент содержит ровно один дочерний `<Metadata>` элемент.

### <a name="packagelanguagepackmanifest-element"></a>Паккажелангуажепаккманифест, элемент

В `<PackageLanguagePackManifest>` элементе должен существовать следующий элемент:

|Заголовок|Описание|
|-----------|-----------------|
|`<Metadata>`| Содержащий элемент для всех локализованных метаданных пакета

### <a name="metadata-element"></a>Элемент Metadata

В `<Metadata>` элементе можно использовать следующие элементы:

|Заголовок|Описание|
|-----------|-----------------|
|`<DisplayName>`|Локализованное имя устанавливаемого расширения|
|`<Description>`|Локализованное описание устанавливаемого расширения|
|`<License>`| Путь к локализованной версии лицензии расширения|
|`<MoreInfo>`| Ссылка на локализованные сведения о расширении|
|`<ReleaseNotes>`| Путь или ссылка на локализованную версию заметок о выпуске|
|`<Icon>`| Путь к локализованной версии значка расширений|

### <a name="sample-manifest"></a>Пример манифеста

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
|[Локализация пакетов VSIX](../extensibility/localizing-vsix-packages.md)|Показывает, как обеспечить поддержку локализованной установки для пакета VSIX.|
|[Справочник по схеме расширения VSIX 2,0](../extensibility/vsix-extension-schema-2-0-reference.md)|Манифест VSIX описывает содержимое файла развертывания *VSIX* . Файл развертывания позволяет установить расширение Visual Studio с помощью диалогового окна **расширения и обновления** .|
|[Поиск и использование расширений Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)|Показывает, как использовать диалоговое окно **расширения и обновления** для установки, удаления, активации и деактивации расширений.|

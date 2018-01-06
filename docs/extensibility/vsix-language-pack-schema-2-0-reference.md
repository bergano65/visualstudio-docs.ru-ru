---
title: "Справочник по схеме 2.0 с пакетом обновления языка VSIX | Документы Microsoft"
ms.custom: 
ms.date: 10/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language pack
- localize vsix
- localize package
- localize extension
ms.assetid: 2a2932bc-cdbe-4d32-91fa-a3e0474f9098
caps.latest.revision: "8"
ms.author: dagriffe
author: dgriffen
manager: ghogen
ms.workload: dagriffe
ms.openlocfilehash: b601653e4b2d309d41f32ff71666567ab860e698
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="vsix-language-pack-schema-20-reference"></a>Справочник по схеме 2.0 с пакетом обновления языка VSIX

Схема языкового пакета VSIX предоставляет локализованные сведения об установке для пакетов VSIX. Эта схема версии 2.0 поддерживает локализации дополнительные элементы.

## <a name="language-pack-schema"></a>Схема языкового пакета

Корневой элемент файла пакета языка — `<PackageLanguagePackManifest>`, с атрибутом `Version`, представляющую собой версию формата пакета языка. В этом разделе описывается пакет язык, который указывается в манифесте, задав версии 2.0 `Version` равным значению `Version="2.0.0"`. Корневой элемент содержит только одну дочернюю `<Metadata>` элемента.

### <a name="packagelangaugepackmanifest-element"></a>Элемент PackageLangaugePackManifest

В пределах `<PackageLanguagePackManifest>` элемент должен существовать следующий элемент:
|Заголовок|Описание:|
|-----------|-----------------|
|`<Metadata>`| Элемент-контейнер для всех метаданных локализованного пакета

### <a name="metadata-element"></a>Элемент метаданных

В пределах `<Metadata>` элемент может иметь следующие элементы:
|Заголовок|Описание:|
|-----------|-----------------|
|`<DisplayName>`|Локализованное имя расширения должны быть установлены|
|`<Description>`|Локализованное описание расширения должны быть установлены|
|`<License>`| Путь к локализованной версии лицензии расширения|
|`<MoreInfo>`| Ссылка на локализованные сведения о расширении|
|`<ReleaseNotes>`| Путь или ссылку на локализованную версию заметок о выпуске|
|`<Icon>`| Путь к локализованной версии значок расширения|

### <a name="sample-manifest"></a>Пример манифеста

```xml
<?xml version="1.0" encoding="utf-8"?>
<PackageLanguagePackManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011">
  <Metadata>
    <DisplayName>Arbol de Familia</LocalizedName>
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
|[Локализация пакетов VSIX](../extensibility/localizing-vsix-packages.md)|Показано, как для обеспечения поддержки локализованного установочного пакета VSIX.|
|[Справочник по схеме 2.0 расширений VSIX](../extensibility/vsix-extension-schema-2-0-reference.md)|Манифест VSIX описывает содержимое файла развертывания с расширением VSIX, расширение Visual Studio установить с помощью **расширения и обновления** диалоговое окно.|
|[Поиск и использование расширений Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)|Показано, как использовать **расширения и обновления** для установки, удаления, активации и деактивации расширений используется диалоговое окно.|
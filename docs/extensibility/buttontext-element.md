---
title: Элемент ButtonText Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59308feea2002a18662a7c04b95a92a920f934c4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739906"
---
# <a name="buttontext-element"></a>Элемент ButtonText
Это поле позволяет указать текст, который отображается в различных меню. По умолчанию `ButtonText` элемент отображается в контроллерах меню. Элемент `ButtonText` также становится по умолчанию, если другие текстовые поля пусты. Элемент `ButtonText` не может быть пустым, даже если указаны другие текстовые поля.

## <a name="syntax"></a>Синтаксис

```xml
<ButtonText>My Command</ButtonText>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты
 Нет.

### <a name="child-elements"></a>Дочерние элементы
 Нет.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент Strings](../extensibility/strings-element.md)|Группы текстовых `ButtonText` элементов, таких как и `CommandName`.|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение `ButtonText` элемента предоставляет текст, отображаемый для элементов меню, комбо и других элементов пользовательского интерфейса (UI), которые имеют видимый текст.

## <a name="see-also"></a>См. также
- [Таблица команд Visual Studio (.vsct) файлов](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

---
title: Элемент ButtonText | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ButtonText element (VSCT XML schema)
- VSCT XML schema elements, ButtonText
ms.assetid: 56aba884-0356-4894-ae4e-32d3938f6865
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fe2440258e95ad0d61998b24dae54b731a998c47
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321217"
---
# <a name="buttontext-element"></a>Элемент ButtonText
Это поле позволяет указать текст, отображаемый в различные меню. По умолчанию `ButtonText` элемент появляется в контроллеры меню. `ButtonText` Элемент становится значением по умолчанию, если другие текстовые поля будут пусты. `ButtonText` Элемент не может быть пустым, даже если указаны другие текстовые поля.

## <a name="syntax"></a>Синтаксис

```xml
<ButtonText>My Command</ButtonText>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты
 Отсутствует.

### <a name="child-elements"></a>Дочерние элементы
 Отсутствует.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент Strings](../extensibility/strings-element.md)|Группирует элементы текста, таких как `ButtonText` и `CommandName`.|

## <a name="text-value"></a>Текстовое значение
 Текстовое значение `ButtonText` элемент содержит текст, отображаемый для пунктов меню, комбинировать и других элементов пользовательского интерфейса (UI), которые имеют видимым текстом.

## <a name="see-also"></a>См. также
- [Visual Studio командные файлы table (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
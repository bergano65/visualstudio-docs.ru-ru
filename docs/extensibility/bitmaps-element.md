---
title: Элемент bitmaps | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: 74652e1b-fcfa-421b-aa9f-fbc081d3b476
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d247a0df29cb14eec6dffa5e362f23693b59cc99
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56699643"
---
# <a name="bitmaps-element"></a>Элемент bitmaps
Группы [точечный рисунок элемента](../extensibility/bitmap-element.md) элементов.

## <a name="syntax"></a>Синтаксис

```
<Bitmaps>
  <Bitmap>... </Bitmap>
  <Bitmap>... </Bitmap>
</Bitmaps>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|Условие|Необязательный параметр. См. в разделе [условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание:|
|-------------|-----------------|
|[Элемент bitmaps](../extensibility/bitmaps-element.md)|Группирует элементы растрового изображения.|
|[Элемент Bitmap](../extensibility/bitmap-element.md)|Определяет растрового изображения.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание:|
|-------------|-----------------|
|[Элемент Commands](../extensibility/commands-element.md)|Представляет коллекцию команд на панели инструментов для VSPackage.|

## <a name="example"></a>Пример

```
<Bitmaps>
  <Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />
  <Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"
    usedList="1, 2, 3, 4"/>
</Bitmaps>
```

## <a name="see-also"></a>См. также
- [Как добавить элементы пользовательского интерфейса в пакеты VSPackage](../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Команды, меню и панелей инструментов](../extensibility/internals/commands-menus-and-toolbars.md)
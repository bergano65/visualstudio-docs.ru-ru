---
title: Элемент Битмап Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Bitmaps
- Bitmaps element (VSCT XML schema)
ms.assetid: edcd7891-f4e7-416d-809d-5e2eed9f17e4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d663351aad7d381dd5bfe4cbaa0a263cc70b821
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739993"
---
# <a name="bitmap-element"></a>Элемент Bitmap
Определяет бит-карту. Битовая карта загружается либо из ресурса, либо из файла.

## <a name="syntax"></a>Синтаксис

```
<Bitmap guid="guidImages" href="images\MyImage.bmp" usedList="bmp1, bmp2, bmp3" />
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|guid|Обязательный элемент. GUID идентификатора команды GUID/ID.<br /><br /> Атрибут guid для бит-карты не связан ни с какой ГРУППой команд.  Она должна быть уникальной для определения bitmap и не должна использоваться для каких-либо других целей.|
|resID|Идентификатор идентификатора идентификатора команды GUID/ID. Требуется либо resID, либо атрибут href.<br /><br /> Атрибут resID — это идентификатор ресурса, определяющий полосу битовой карты, которая должна быть загружена во время слияния таблиц команд.  При загрузке таблицы команд битов, указанных идентификатором ресурса, с ресурса того же модуля будут загружены.|
|подержанныйСписок|Требуется, если атрибут resID присутствует. Выбирает доступные изображения в полосе bitmap.|
|href|Путь к бит-карте. Требуется либо resID, либо атрибут href.<br /><br /> Путь включения ищется для указанного файла изображения, который встроен в полученный двоичный файл.  Во время слияния таблицы команд изображение скопировано, и не требуется дополнительный поиск или загрузка ресурса.  Если атрибут usedList отсутствует, все изображения в полосе доступны. **Примечание:**  Изображения могут быть предоставлены в одном из нескольких форматов, которые включают *.bmp*, *.png,* и *.gif*.  Более ранние версии компилятора не поддерживали 32-битные изображения битовой карты, которые имели альфа-информацию для частичной прозрачности. Решением для этих версий является использование формата *.png.*|
|Условие|Необязательный параметр. Посмотреть [условные атрибуты.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Дочерние элементы
 Нет.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент Bitmaps](../extensibility/bitmaps-element.md)|Элементы Битмап групп.|

## <a name="example"></a>Пример

```
<Bitmap guid="guidWidgetIcons" href="WidgetToolbarIcons_32.bmp" />
<Bitmap guid="guidWidgetIcons2" resID="IDBMP_WIDGETICONS"
  usedList="1, 2, 3, 4"/>
```

## <a name="see-also"></a>См. также
- [Таблица команд Visual Studio (.vsct) файлов](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

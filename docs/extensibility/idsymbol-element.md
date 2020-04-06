---
title: Элемент IDSymbol Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDSymbol element (VSCT XML schema)
- VSCT XML schema elements, IDSymbol
ms.assetid: 760cfd20-3c06-422c-9103-98bfa1f387f8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d02a26a6874165738d917a14986d16d142c01915
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710377"
---
# <a name="idsymbol-element"></a>Элемент IDSymbol
Элемент `IDSymbol` содержит идентификатор пары GUID:ID, представляющий меню, группу или команду. GUID происходит от `GuidSymbol` родительского элемента. Элемент `IDSymbol` имеет `name` атрибут, который предоставляет дружественное имя для идентификатора, которое содержится в атрибуте. `value`

## <a name="syntax"></a>Синтаксис

```xml
<IDSymbol name=ElementName value="0x0010" />
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|name|Обязательный элемент. Название символа ID.|
|value|Обязательный элемент. Значение числа идентификатора символа идентификатора.|

### <a name="child-elements"></a>Дочерние элементы
 Нет.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент GuidSymbol](../extensibility/guidsymbol-element.md)|Содержит GUID пары GUID:ID, представляющую меню, группу или команду. Группирует элементы `IDSymbol`.|

## <a name="remarks"></a>Примечания
 Каждый `IDSymbol` элемент `GuidSymbol` в данном элементе должен иметь уникальный. `value` Тем `IDSymbol` не менее, элементы, которые имеют одинаковые значения могут существовать в пакете до тех пор, пока у них есть разные родители.

## <a name="see-also"></a>См. также
- [Таблица команд Visual Studio (.vsct) файлов](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

---
title: Элемент Гидсимвола Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 59068a9ac9f952b5370681b3684ce4234354afc9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711132"
---
# <a name="guidsymbol-element"></a>Элемент GuidSymbol
Элемент `GuidSymbol` содержит GUID пары GUID:ID, представляющую меню, группу или команду. Идентификатор `IDSymbol` происходит `GuidSymbol` от элемента элемента элемента. Элемент `GuidSymbol` имеет `name` атрибут, который предоставляет дружественное название для GUID, которое содержится в атрибуте. `value`

## <a name="syntax"></a>Синтаксис

```xml
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">
  <IDSymbol>... </IDSymbol>
  <IDSymbol>... </IDSymbol>
</GuidSymbol>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|name|Обязательный элемент. Название символа GUID.|
|value|Обязательный элемент. GUID символа GUID.|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент IDSymbol](../extensibility/idsymbol-element.md)|Содержит идентификатор пары GUID:ID, представляющий меню, группу или команду.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент символов](../extensibility/symbols-element.md)|Группирует `GuidSymbol` элементы в файле *.vsct.*|

## <a name="remarks"></a>Примечания
 Как правило, файл *.vsct* содержит три `GuidSymbol` элемента в своем `Symbols` разделе, один для самого пакета, один для набора команд (сбор меню, групп и команд, которые предоставляетпакет), и один для битовых карт, которые предоставляют значки для кнопок и других визуальных компонентов. Каждый `IDSymbol` элемент `GuidSymbol` в данном элементе должен иметь уникальный. `value` Тем `IDSymbol` не менее, элементы, которые имеют одинаковые значения могут существовать в пакете до тех пор, пока у них есть разные родители.

## <a name="see-also"></a>См. также
- [Таблица команд Visual Studio (.vsct) файлов](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

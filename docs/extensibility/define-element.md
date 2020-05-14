---
title: Определить элемент Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, Define
- Define element (VSCT XML schema)
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fc09de1d822f41b25397c7a56c7cce4449a9e551
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712273"
---
# <a name="define-element"></a>Определить элемент
Определяет имя символа и пару значений. Этот символ можно оценить по условным атрибутам. Для получения дополнительной [информации см.](../extensibility/vsct-xml-schema-conditional-attributes.md) Смотрите также [элемент Символы](../extensibility/symbols-element.md).

## <a name="syntax"></a>Синтаксис

```
<Define name="Mode" value="Standard" />
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|name|Обязательный элемент. Название символа:<br /><br /> имя»Mode"|
|value|Обязательный элемент. Значение символа:<br /><br /> значение»Стандарт"|
|Условие|Необязательный параметр. Для получения дополнительной [информации см.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Дочерние элементы
 Нет.

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент CommandTable](../extensibility/commandtable-element.md)|Определяет все элементы, представляющие команды, которые VSPackage предоставляет интегрированной среде разработки (IDE). Например, пункты меню, меню, панели инструментов и комбо-коробки.|

## <a name="example"></a>Пример

```
<Define name="DEMO_UI"/>
<Define name="MODE" value="Standard"/>
```

## <a name="see-also"></a>См. также
- [Таблица команд Visual Studio (.vsct) файлов](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

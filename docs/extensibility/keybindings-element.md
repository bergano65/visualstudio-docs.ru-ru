---
title: Элемент keyBindings (англ.) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- KeyBindings
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBindings element (VSCT XML schema)
ms.assetid: 26a15d5c-ddea-4977-af7f-d795ff09c7ad
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: df1720286007d8f6acf073c21f5b2dcc8486782c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703129"
---
# <a name="keybindings-element"></a>Элемент KeyBindings
Элемент KeyBindings группирует элементы KeyBinding и другие группировки KeyBindings.

## <a name="syntax"></a>Синтаксис

```xml
<KeyBindings>
  <KeyBinding>... </KeyBinding>
  <KeyBinding>... </KeyBinding>
</KeyBindings>
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|Условие|Необязательный параметр. Посмотреть [условные атрибуты.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент KeyBinding](../extensibility/keybinding-element.md)|Определяет клавиши для команд.|
|[Ключевые привязки](../extensibility/keybindings-element.md)|Группы элементов KeyBinding и другие группировки KeyBindings.|

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент CommandTable](../extensibility/commandtable-element.md)|Определяет все элементы, представляющие команды.|

## <a name="example"></a>Пример

```xml
<KeyBindings>
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"
    editor="guidWidgetEditor" key1="VK_F5"/>
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>
</KeyBindings>
```

## <a name="see-also"></a>См. также
- [Элемент KeyBinding](../extensibility/keybinding-element.md)
- [Таблица команд Visual Studio (.vsct) файлов](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

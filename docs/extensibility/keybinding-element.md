---
title: Элемент настраиваемое сочетание клавиш | Документация Майкрософт
description: Элемент настраиваемое сочетание клавиш задает сочетания клавиш для команд. С командами могут быть связаны как одинарные, так и двойные привязки.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 2ce96da36a8c6eff0fda71d8a5d077721876ab8b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99943352"
---
# <a name="keybinding-element"></a>Настраиваемое сочетание клавиш, элемент
Элемент настраиваемое сочетание клавиш задает сочетания клавиш для команд.

 С командами могут быть связаны как одинарные, так и двойные привязки. Примером однозначной привязки является **сочетание клавиш CTRL** + **S** для команды **Save** . Для запуска команды с двойными сочетаниями клавиш требуются две последовательные комбинации ключей. Примером двойной привязки является <strong>CTRL *+</strong> k <strong>,</strong>Ctrl <strong>+</strong> k** для установки закладки.

## <a name="syntax"></a>Синтаксис

```
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />
```

## <a name="attributes-and-elements"></a>Элементы и атрибуты
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.

### <a name="attributes"></a>Атрибуты

|Атрибут|Описание|
|---------------|-----------------|
|guid|Обязательный элемент.|
|идентификатор|Обязательный элемент.|
|редактор|Обязательный элемент. GUID редактора указывает контекст редактирования, для которого это сочетание клавиш будет активно. Значение области глобальной привязки — "guidVSStd97".|
|key1|Обязательный элемент. Допустимые значения включают все буквенно-цифровые типабле, а также двузначные шестнадцатеричные значения, начинающиеся с 0x и [VK_constants](/windows/desktop/inputdev/virtual-key-codes).|
|mod1|Необязательный элемент. Любое сочетание **клавиш CTRL**, **ALT** и **SHIFT** , разделенное пробелом.|
|key2|Необязательный элемент. Допустимые значения включают все буквенно-цифровые типабле, а также двузначные шестнадцатеричные значения, начинающиеся с 0x и [VK_constants](/windows/desktop/inputdev/virtual-key-codes).|
|mod2|Необязательный элемент. Любое сочетание **клавиш CTRL**, **ALT** и **SHIFT** , разделенное пробелом.|
|эмулятор|Необязательный элемент.|
|Условие|Необязательный элемент. См. раздел [Условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|Parent||
|Annotation||

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Сочетания клавиш, элемент](../extensibility/keybindings-element.md)|Группирует элементы настраиваемое сочетание клавиш и другие группирования сочетания клавиш.|

## <a name="example"></a>Пример

```
<KeyBindings>
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"
    editor="guidWidgetEditor" key1="VK_F5"/>
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>
</KeyBindings>
```

## <a name="see-also"></a>См. также раздел
- [Сочетания клавиш, элемент](../extensibility/keybindings-element.md)
- [Файлы таблицы команд Visual Studio (. vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

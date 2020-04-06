---
title: Элемент keyBinding (англ.) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b458e70a9a85c11707c50da2e16e3aa73f51bc12
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703143"
---
# <a name="keybinding-element"></a>Элемент KeyBinding
Элемент KeyBinding определяет ярлыки клавиатуры для команд.

 Команды могут иметь как одиночные, так и двойные ключевые привязки, связанные с ними. Примером одного связывания ключа является **Ctrl**+**S** для команды **Save.** Двойные крепления ключей требуют двух последовательных комбинаций ключей для запуска команды. Примером двойного связывания ключа является <strong>Ctrl*+</strong><strong>K,</strong><strong>+</strong>Ctrl K,* чтобы установить закладку.

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
|редактор|Обязательный элемент. Редактор GUID указывает контекст редактирования, для которого этот ярлык клавиатуры будет активен. Глобальное значение обязательной сферы является "guidVSStd97".|
|key1|Обязательный элемент. Допустимые значения включают все опечатанные алфавиты, а также двузначные гексадецимальные значения, которым предшествовали 0x и [VK_constants.](/windows/desktop/inputdev/virtual-key-codes)|
|mod1|Необязательный параметр. Любая комбинация **Ctrl,** **Alt**и **Shift** разделена пространством.|
|key2|Необязательный параметр. Допустимые значения включают все опечатанные алфавиты, а также двузначные гексадецимальные значения, которым предшествовали 0x и [VK_constants.](/windows/desktop/inputdev/virtual-key-codes)|
|mod2|Необязательный параметр. Любая комбинация **Ctrl,** **Alt**и **Shift** разделена пространством.|
|эмулятор|Необязательный параметр.|
|Условие|Необязательный параметр. Посмотреть [условные атрибуты.](../extensibility/vsct-xml-schema-conditional-attributes.md)|

### <a name="child-elements"></a>Дочерние элементы

|Элемент|Описание|
|-------------|-----------------|
|Parent||
|Заметка||

### <a name="parent-elements"></a>Родительские элементы

|Элемент|Описание|
|-------------|-----------------|
|[Элемент KeyBindings](../extensibility/keybindings-element.md)|Группы элементов KeyBinding и другие группировки KeyBindings.|

## <a name="example"></a>Пример

```
<KeyBindings>
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"
    editor="guidWidgetEditor" key1="VK_F5"/>
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>
</KeyBindings>
```

## <a name="see-also"></a>См. также
- [Элемент KeyBindings](../extensibility/keybindings-element.md)
- [Таблица команд Visual Studio (.vsct) файлов](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

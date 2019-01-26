---
title: Элемент KeyBinding | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4706114f87e18ce97789e41098e13cf38917d533
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54933043"
---
# <a name="keybinding-element"></a>Элемент KeyBinding
Элемент KeyBinding указывает сочетания клавиш для команд.  
  
 Команды могут иметь одного или двух привязок клавиш, связанных с ними. Пример одной привязки ключей — **Ctrl**+**S** для **Сохранить** команды. Двойной сочетания клавиш требуют двух последовательных сочетания клавиш для запуска команды. Пример двойного привязки ключей — <strong>Ctrl*+</strong>K<strong>,</strong>Ctrl<strong>+</strong>K** Чтобы установить закладку.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />  
```  
  
## <a name="attributes-and-elements"></a>Элементы и атрибуты  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|guid|Обязательный.|  
|id|Обязательный.|  
|редактор|Обязательный. Идентификатор GUID редактора указывает контекст редактирования, для которого будет всегда активной это сочетание клавиш. Значение области действия глобального привязки — «guidVSStd97».|  
|key1|Обязательный. Допустимыми являются все прочтения буквенно-цифровые символы, а также шестнадцатеричные значения из двух цифр, предшествует 0 x и [VK_constants](/windows/desktop/inputdev/virtual-key-codes).|  
|MOD1|Необязательный параметр. Любое сочетание **Ctrl**, **Alt**, и **Shift** разделяются пробелами.|  
|key2|Необязательный параметр. Допустимыми являются все прочтения буквенно-цифровые символы, а также шестнадцатеричные значения из двух цифр, предшествует 0 x и [VK_constants](/windows/desktop/inputdev/virtual-key-codes).|  
|MOD2|Необязательный параметр. Любое сочетание **Ctrl**, **Alt**, и **Shift** разделяются пробелами.|  
|Эмулятор|Необязательный параметр.|  
|Условие|Необязательный параметр. См. в разделе [условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание:|  
|-------------|-----------------|  
|Родительский||  
|Комментарий||  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание:|  
|-------------|-----------------|  
|[Элемент KeyBindings](../extensibility/keybindings-element.md)|Группирует элементы сочетание клавиш и другими признаками сочетания клавиш.|  
  
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
 [Элемент KeyBindings](../extensibility/keybindings-element.md)   
 [Visual Studio командные файлы table (.vsct)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

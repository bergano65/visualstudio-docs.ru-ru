---
title: Элемент KeyBinding | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3b5e35738f04dd4a05a753a58e91ca385ecd56bd
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/08/2018
ms.locfileid: "39639328"
---
# <a name="keybinding-element"></a>Элемент KeyBinding
Элемент KeyBinding указывает сочетания клавиш для команд.  
  
 Команды могут иметь одного или двух привязок клавиш, связанных с ними. Пример одной привязки ключей — **Ctrl**+**S** для **Сохранить** команды. Двойной сочетания клавиш требуют двух последовательных сочетания клавиш для запуска команды. Пример двойного привязки ключей — **Ctrl * +** K **,** Ctrl**+** K **, чтобы установить закладку.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />  
```  
  
## <a name="attributes-and-elements"></a>Элементы и атрибуты  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание:|  
|---------------|-----------------|  
|guid|Обязательно.|  
|id|Обязательно.|  
|редактор|Обязательно. Идентификатор GUID редактора указывает контекст редактирования, для которого будет всегда активной это сочетание клавиш. Значение области действия глобального привязки — «guidVSStd97».|  
|key1|Обязательно. Допустимыми являются все прочтения буквенно-цифровые символы, а также шестнадцатеричные значения из двух цифр, предшествует 0 x и [VK_constants](https://msdn.microsoft.com/library/windows/desktop/dd375731.aspx).|  
|MOD1|Необязательный. Любое сочетание **Ctrl**, **Alt**, и **Shift** разделяются пробелами.|  
|key2|Необязательный. Допустимыми являются все прочтения буквенно-цифровые символы, а также шестнадцатеричные значения из двух цифр, предшествует 0 x и [VK_constants](https://msdn.microsoft.com/library/windows/desktop/dd375731.aspx).|  
|MOD2|Необязательный. Любое сочетание **Ctrl**, **Alt**, и **Shift** разделяются пробелами.|  
|Эмулятор|Необязательный.|  
|Условие|Необязательный. См. в разделе [условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
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

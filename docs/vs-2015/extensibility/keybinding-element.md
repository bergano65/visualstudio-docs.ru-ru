---
title: Элемент KeyBinding | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7dd7f56a91661850a3154ad09376340696513646
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573384"
---
# <a name="keybinding-element"></a>Элемент KeyBinding
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [элемент KeyBinding](https://docs.microsoft.com/visualstudio/extensibility/keybinding-element).  
  
Элемент KeyBinding указывает сочетания клавиш для команд.  
  
 Команды могут иметь одного или двух привязок клавиш, связанных с ними. Пример одной привязки ключей — CTRL + S для **Сохранить** команды. Двойной сочетания клавиш требуют двух последовательных сочетания клавиш для запуска команды. Пример двойную привязку клавиш — CTRL + K, CTRL + K, чтобы установить закладку.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|guid|Обязательно.|  
|id|Обязательно.|  
|редактор|Обязательно. Идентификатор GUID редактора указывает контекст редактирования, для которого будет всегда активной это сочетание клавиш. Значение области действия глобального привязки — «guidVSStd97».|  
|key1|Обязательно. Допустимые значения включают все прочтения буквенно-цифровые символы, а также шестнадцатеричные значения из двух цифр, предшествующим 0 x и VK_constants.|  
|MOD1|Необязательный. Любое сочетание CTRL, ALT и SHIFT разделяются пробелами.|  
|key2|Необязательный. Допустимые значения включают все прочтения буквенно-цифровые символы, а также шестнадцатеричные значения из двух цифр, предшествующим 0 x и VK_constants.|  
|MOD2|Необязательный. Любое сочетание CTRL, ALT и SHIFT разделяются пробелами.|  
|Эмулятор|Необязательный.|  
|Условие|Необязательный. См. в разделе [условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|Родительский||  
|Комментарий||  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
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
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)


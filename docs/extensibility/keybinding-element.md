---
title: Элемент соответствующие клавиши | Документы Microsoft
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
ms.openlocfilehash: 226a5913cbaa151689a886dc88986f7de8cc29f6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="keybinding-element"></a>Элемент соответствующие клавиши
Элемент соответствующие клавиши указывает сочетания клавиш для команд.  
  
 Команды могут иметь одного и обоих сочетания клавиш, связанных с ними. Пример одной привязки ключей — CTRL + S для **Сохранить** команды. Двойная сочетания клавиш требуют двух последовательных сочетаний клавиш для запуска команды. Пример двойного привязки ключей — CTRL + K, CTRL + K, чтобы установить закладку.  
  
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
|редактор|Обязательно. Редактор GUID показывает контекст редактирования, для которого это сочетание клавиш будет активным. Значение области действия глобальные привязки — «guidVSStd97».|  
|key1|Обязательно. Допустимые значения включают все прочтения буквы и цифры, а также шестнадцатеричные значения двух цифр, знаком 0 x и [VK_constants](https://msdn.microsoft.com/en-us/library/windows/desktop/dd375731.aspx).|  
|MOD1|Необязательный. Любое сочетание CTRL, ALT и клавишу SHIFT, через пробел.|  
|key2|Необязательный. Допустимые значения включают все прочтения буквы и цифры, а также шестнадцатеричные значения двух цифр, знаком 0 x и [VK_constants](https://msdn.microsoft.com/en-us/library/windows/desktop/dd375731.aspx).|  
|MOD2|Необязательный. Любое сочетание CTRL, ALT и клавишу SHIFT, через пробел.|  
|эмулятор|Необязательный.|  
|Условие|Необязательный. В разделе [условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|Родительский||  
|Комментарий||  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент KeyBindings](../extensibility/keybindings-element.md)|Группирует элементы соответствующие клавиши и других группирований сочетания клавиш.|  
  
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
 [Элемент привязки клавиш](../extensibility/keybindings-element.md)   
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

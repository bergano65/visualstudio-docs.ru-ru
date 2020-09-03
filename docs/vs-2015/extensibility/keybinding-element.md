---
title: Элемент настраиваемое сочетание клавиш | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 75d96098e8444aac9a4fc6f895099435b54f640b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180331"
---
# <a name="keybinding-element"></a>Элемент KeyBinding
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Элемент настраиваемое сочетание клавиш задает сочетания клавиш для команд.  
  
 С командами могут быть связаны как одинарные, так и двойные привязки. Примером однозначной привязки является сочетание клавиш CTRL + S для команды **Save** . Для запуска команды с двойными сочетаниями клавиш требуются две последовательные комбинации ключей. Примером двойной привязки является CTRL + K, CTRL + K для установки закладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```  
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />  
```  
  
## <a name="attributes-and-elements"></a>Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### <a name="attributes"></a>Атрибуты  
  
|Атрибут|Описание|  
|---------------|-----------------|  
|guid|Обязательный.|  
|идентификатор|Обязательный.|  
|редактор|Обязательный. GUID редактора указывает контекст редактирования, для которого это сочетание клавиш будет активно. Значение области глобальной привязки — "guidVSStd97".|  
|key1|Обязательный. Допустимые значения включают все буквенно-цифровые типабле, а также двузначные шестнадцатеричные значения, начинающиеся с 0x и VK_constants.|  
|mod1|Необязательный элемент. Любое сочетание клавиш CTRL, ALT и SHIFT, разделенное пробелом.|  
|key2|Необязательный элемент. Допустимые значения включают все буквенно-цифровые типабле, а также двузначные шестнадцатеричные значения, начинающиеся с 0x и VK_constants.|  
|mod2|Необязательный элемент. Любое сочетание клавиш CTRL, ALT и SHIFT, разделенное пробелом.|  
|эмулятор|Необязательный элемент.|  
|Условие|Необязательный элемент. См. раздел [Условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### <a name="child-elements"></a>Дочерние элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|Parent||  
|Заметка||  
  
### <a name="parent-elements"></a>Родительские элементы  
  
|Элемент|Описание|  
|-------------|-----------------|  
|[Элемент KeyBindings](../extensibility/keybindings-element.md)|Группирует элементы настраиваемое сочетание клавиш и другие группирования сочетания клавиш.|  
  
## <a name="example"></a>Пример  
  
```  
<KeyBindings>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"   
    editor="guidWidgetEditor" key1="VK_F5"/>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"   
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>  
</KeyBindings>  
```  
  
## <a name="see-also"></a>См. также:  
 [Сочетания клавиш, элемент](../extensibility/keybindings-element.md)   
 [Файлы таблицы команд Visual Studio (VSCT-файлы)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

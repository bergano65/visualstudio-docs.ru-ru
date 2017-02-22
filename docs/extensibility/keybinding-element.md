---
title: "Элемент соответствующие клавиши | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Элементы схемы VSCT XML, сочетания клавиш"
  - "Элемент соответствующие клавиши (VSCT XML-схемы)"
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Элемент соответствующие клавиши
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Элемент соответствующие клавиши задает сочетания клавиш для команд.  
  
 Команды могут иметь одной или двух привязок клавиш, связанных с ними. Пример одной привязки клавиш: CTRL \+ S для **Сохранить** команды. Два ключа привязки требуют двух последовательных сочетаний клавиш для запуска команды. Пример двух привязки клавиш: CTRL \+ K,CTRL \+ K, чтобы установить закладку.  
  
## Синтаксис  
  
```  
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|Идентификатор GUID|Обязательный.|  
|id|Обязательный.|  
|редактор|Обязательный. Редактор GUID указывает контекст редактирования, для которого это сочетание клавиш будет активным. Область глобального привязки значение «guidVSStd97».|  
|key1|Обязательный. Допустимые значения включают все прочтения буквы и цифры, а также предшествует 0 x и VK\_constants шестнадцатеричных значений двух цифр.|  
|MOD1|Необязательный. Любое сочетание CTRL, ALT или SHIFT, разделенных пробелами.|  
|key2|Необязательный. Допустимые значения включают все прочтения буквы и цифры, а также предшествует 0 x и VK\_constants шестнадцатеричных значений двух цифр.|  
|MOD2|Необязательный. Любое сочетание CTRL, ALT или SHIFT, разделенных пробелами.|  
|эмулятор|Необязательный.|  
|Условие|Необязательный. См. раздел [Условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Дочерние элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|Родительский||  
|Комментарий||  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[Элемент привязки клавиш](../extensibility/keybindings-element.md)|Группирует элементы соответствующие клавиши и других группирований сочетания клавиш.|  
  
## Пример  
  
```  
<KeyBindings> <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget" editor="guidWidgetEditor" key1="VK_F5"/> <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget" editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/> </KeyBindings>  
```  
  
## См. также  
 [Элемент привязки клавиш](../extensibility/keybindings-element.md)   
 [Таблицы команд Visual Studio \(. Файлы Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
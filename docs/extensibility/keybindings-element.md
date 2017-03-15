---
title: "Элемент привязки клавиш | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "KeyBindings"
helpviewer_keywords: 
  - "Элементы схемы VSCT XML, сочетания клавиш"
  - "Элемент привязки клавиш (VSCT XML-схемы)"
ms.assetid: 26a15d5c-ddea-4977-af7f-d795ff09c7ad
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Элемент привязки клавиш
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Элемент привязки клавиш группирует элементы соответствующие клавиши и других группирований сочетания клавиш.  
  
## Синтаксис  
  
```  
<KeyBindings>  
  <KeyBinding>... </KeyBinding>  
  <KeyBinding>... </KeyBinding>  
</KeyBindings>  
```  
  
## Атрибуты и элементы  
 В следующих разделах описаны атрибуты, дочерние и родительские элементы.  
  
### Атрибуты  
  
|Атрибут|Описание|  
|-------------|--------------|  
|Условие|Необязательный. См. раздел [Условные атрибуты](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Дочерние элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[Элемент соответствующие клавиши](../extensibility/keybinding-element.md)|Задает сочетания клавиш для команд.|  
|[KeyBindings](../extensibility/keybindings-element.md)|Группирует элементы соответствующие клавиши и других группирований сочетания клавиш.|  
  
### Родительские элементы  
  
|Элемент|Описание|  
|-------------|--------------|  
|[Элемент CommandTable](../extensibility/commandtable-element.md)|Определяет все элементы, представляющие команды.|  
  
## Пример  
  
```  
<KeyBindings> <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget" editor="guidWidgetEditor" key1="VK_F5"/> <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget" editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/> </KeyBindings>  
```  
  
## См. также  
 [Элемент соответствующие клавиши](../extensibility/keybinding-element.md)   
 [Таблицы команд Visual Studio \(. Файлы Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
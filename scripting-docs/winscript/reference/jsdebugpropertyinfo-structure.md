---
title: "Структура JsDebugPropertyInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: JsDebugPropertyInfo
apilocation: jscript9diag.dll
ms.assetid: 3a5463a7-2013-4846-9ab2-8beb675a5a6a
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Структура JsDebugPropertyInfo
Задает сведения о свойстве.  
  
## Синтаксис  
  
```  
typedef struct tagJsDebugPropertyInfo  
{  
   BSTR name;  
   BSTR type;  
   BSTR value;  
   BSTR fullName;  
   JS_PROPERTY_ATTRIBUTES attr;  
} JsDebugPropertyInfo;  
```  
  
## Члены  
 `name`  
 Имя свойства.  
  
 `type`  
 Тип свойства.  
  
 `value`  
 Значение свойства.  
  
 `fullName`  
 Полное имя свойства.  
  
 `attr`  
 Перечисление, представляющее атрибуты свойства.  
  
## Требования  
 **Заголовок:** jscript9diag.h  
  
## См. также  
 [Справочник по интерфейсам скриптов Windows](../../winscript/reference/windows-script-interfaces-reference.md)
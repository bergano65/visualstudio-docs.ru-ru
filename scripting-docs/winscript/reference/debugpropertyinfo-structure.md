---
title: "Структура DebugPropertyInfo | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: DebugPropertyInfo
apilocation: scrobj.dll
helpviewer_keywords: 
  - "DebugPropertyInfo — структура"
ms.assetid: 3246efbc-c212-4024-8f07-6414c2f85e75
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Структура DebugPropertyInfo
Описывает объект иерархической характера, которая имеет имя, тип и значение.  Она используется для описания свойств отладки локальных переменных, параметров и выражений, переменных в контрольных значениях и регистры.  
  
## Синтаксис  
  
```  
typedef struct DebugPropertyInfo{  
   DBGPROP_INFO_FLAGS  dwValidFields;  
   BSTR  bstrName;  
   BSTR  bstrType;  
   BSTR  bstrValue;  
   BSTR  bstrFullName;  
   DBGPROP_ATTRIB_FLAGS  dwAttrib;  
   IDebugProperty*  pDebugProp;  
};  
```  
  
## Члены  
 dwValidFields  
 Перечислимые типы данных, используемый для определения того, какие поля инициализироватьы.  
  
 bstrName  
 Имя свойства в контексте.  
  
 bstrType  
 Тип свойства, например форматированная строка.  
  
 bstrValue  
 Значение свойства, например форматированная строка.  
  
 bstrFullName  
 Полное имя свойства.  
  
 dwAttrib  
 Перечисление, указывающее флаги для свойства отладки приписывает.  
  
 pDebugProp  
 Сведения `IDebugProperty`, описанное в этой структуре `DebugPropertyInfo`.  
  
## См. также  
 [Интерфейс IDebugProperty](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP\_ATTRIB\_FLAGS](../../winscript/reference/dbgprop-attrib-flags.md)   
 [DBGPROP\_INFO\_FLAGS](../../winscript/reference/dbgprop-info-flags.md)
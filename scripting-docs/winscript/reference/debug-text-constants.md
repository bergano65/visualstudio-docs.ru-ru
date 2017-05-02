---
title: "Константы DEBUG_TEXT | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 5dde10c3-7040-46b1-a328-959c6ce5cd9f
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Константы DEBUG_TEXT
Используется во время [IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md).  
  
## Синтаксис  
  
```  
typedef DWORD DEBUG_TEXT;  
  
```  
  
## Константы  
  
|Константа|Значение|Описание|  
|---------------|--------------|--------------|  
|DWORD DEBUG\_TEXT\_ISEXPRESSION|0x00000001|Указывает, что текст выражения в отличие от выписки.  Этот флажок может повлиять на способ, которым текст выделяется несколькими языками.|  
|DEBUG\_TEXT\_RETURNVALUE|0x00000002|Если возвращаемое значение доступно, оно будет использоваться вызывающим объектом.|  
|DEBUG\_TEXT\_NOSIDEEFFECTS|0x00000004|Не допускайте побочные эффекты.  Если этот флажок установлен, то вычисление выражения не должны изменяться нет состояния среды выполнения.|  
|DEBUG\_TEXT\_ALLOWBREAKPOINTS|0x00000008|Разрешать точки останова во время обработки текста.  Если этот флажок не установлен, точки останова будут пропущены во время обработки текста.|  
|DEBUG\_TEXT\_ALLOWERRORREPORT|0x00000010|Разрешите отчетов ошибки во время обработки текста.  Если этот флажок не установлен, то ошибки не будут отражены в узел во время вычисления.|  
|DEBUG\_TEXT\_EVALUATETOCODECONTEXT|0x00000020|Указывает, что необходимо оценить выражение к контексту кода, а не ход само выражение.|  
  
## См. также  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)
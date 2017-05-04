---
title: "Структура JS_NATIVE_FRAME | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: JS_NATIVE_FRAME
apilocation: jscript9diag.dll
ms.assetid: 5afa2ee1-b3e2-47cb-b304-84f96e6fbb14
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Структура JS_NATIVE_FRAME
Предоставляет кадр стека.  
  
## Синтаксис  
  
```  
typedef struct {  
    UINT64 InstructionOffset;  
    UINT64 ReturnOffset;  
    UINT64 FrameOffset;  
    UINT64 StackOffset;  
} JS_NATIVE_FRAME;  
```  
  
## Члены  
 `InstructionOffset`  
 Указатель инструкции.  
  
 `ReturnOffset`  
 Обратный адрес.  
  
 `FrameOffset`  
 Указатель кадра.  
  
 `StackOffset`  
 Указатель стека.  
  
## Заметки  
 Структура `JS_NATIVE_FRAME` используется классом `IJsStackFrameEnumerator`.  
  
## См. также  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)
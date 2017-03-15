---
title: "StackFrameTypeEnum | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "StackFrameTypeEnum - перечисление"
ms.assetid: 61e40163-eee0-4c1f-af47-cef3771bdc41
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# StackFrameTypeEnum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Указывает тип кадра стека.  
  
## Синтаксис  
  
```cpp  
enum StackFrameTypeEnum {  
   FrameTypeFPO,  
   FrameTypeTrap,  
   FrameTypeTSS,  
   FrameTypeStandard,  
   FrameTypeFrameData,  
   FrameTypeUnknown = -1  
};  
```  
  
## Elements  
 `FrameTypeFPO`  
 Снятый указатель кадра; FPO доступные данные.  
  
 `FrameTypeTrap`  
 Кадр ловушки ядра.  
  
 `FrameTypeTSS`  
 Кадр ловушки ядра.  
  
 `FrameTypeStandard`  
 Стандартный кадр стека EBP.  
  
 `FrameTypeFrameData`  
 Снятый указатель кадра; Доступ к данным по данным кадра.  
  
 `FrameTypeUnknown`  
 Кадр, который не имеет каких\-либо отладки сведения.  
  
## Заметки  
 Значения в этом перечислении возвращаемых вызовом [IDiaStackFrame::get\_type](../../debugger/debug-interface-access/idiastackframe-get-type.md) метод.  
  
## Требования  
 Заголовок: cvconst.h  
  
## См. также  
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackFrame::get\_type](../../debugger/debug-interface-access/idiastackframe-get-type.md)
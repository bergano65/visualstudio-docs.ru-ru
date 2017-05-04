---
title: "Структура DebugStackFrameDescriptor | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: DebugStackFrameDescriptor
apilocation: scrobj.dll
helpviewer_keywords: 
  - "DebugStackFrameDescriptor — структура"
ms.assetid: a86bcb99-41e4-4a26-a1dd-e1458fb73139
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Структура DebugStackFrameDescriptor
Перечисляет кадры стека и объединяет выходные данные из нескольких перечислителей на одном и том же потоке.  
  
## Синтаксис  
  
```  
typedef struct tagDebugStackFrameDescriptor {  
   IDebugStackFrame *pdsf;  
   DWORD_PTR        dwMin;  
   DWORD_PTR        dwLim;  
   BOOL             fFinal;  
   IUnknown         *punkFinal;  
} DebugStackFrameDescriptor;  
```  
  
## Члены  
 `pdsf`  
 Объект кадра стека.  
  
 `dwMin`  
 Представление компьютер\- зависимых более низкого диапазона физических адресов, связанный с данным кадром стека.  
  
 `dwLim`  
 Представление компьютер\- зависимых верхнего диапазона физических адресов, связанный с данным кадром стека.  
  
 `fFinal`  
 Пометьте, которое указывает на то, что кадр обрабатывается.  
  
 `punkFinal`  
 Если этот параметр не `NULL`, текущий слияние перечислителя должен остановить и новое должно быть запуститьо.  Объект показано, как запустить новое перечисление.  
  
## Заметки  
 Процесс отладки использования диспетчера эта структура сортировки кадры стека из нескольких обработчиков скриптов.  По соглашению стеки растут вниз.  Следовательно, на архитектурах, где стеки растут вверх, адреса должны быть укомплектованы.  
  
## См. также  
 [Константы, перечисления и структуры отладчика активных скриптов](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)
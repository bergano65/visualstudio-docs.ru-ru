---
title: "IDebugThread2::SetNextStatement | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugThread2::SetNextStatement"
helpviewer_keywords: 
  - "IDebugThread2::SetNextStatement"
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugThread2::SetNextStatement
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Задает текущий указатель инструкций к заданному контексту кода.  
  
## Синтаксис  
  
```cpp#  
HRESULT SetNextStatement (   
   IDebugStackFrame2*  pStackFrame,  
   IDebugCodeContext2* pCodeContext  
);  
```  
  
```c#  
int SetNextStatement (   
   IDebugStackFrame2  pStackFrame,  
   IDebugCodeContext2 pCodeContext  
);  
```  
  
#### Параметры  
 `pStackFrame`  
 Зарезервировано для использования в будущем. установите в значение NULL.  
  
 `pCodeContext`  
 \[in\] IDebugCodeContext2 объект, описывающий расположение кода, который выполняется, и его контекст.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  В следующей таблице приведены другие возможные значения.  
  
|Значение|Описание|  
|--------------|--------------|  
|\_SET\_NEXT\_STATEMENT\_ON\_NONLEAF\_FRAME НЕ E\_CAN|Следующий оператор не может находиться в кадре стека более глубоком в стеке кадра.|  
|\_SETIP\_TO\_DIFFERENT\_FUNCTION НЕ E\_CAN|Следующий оператор не связана с одним кадром в стеке.|  
|\_SET\_NEXT\_STATEMENT\_ON\_EXCEPTION НЕ E\_CAN|Некоторые обработчики отладки не может установить следующей выписку после исключения.|  
  
## Заметки  
 Указатель инструкции отображаются следующие инструкции или выписку выполнения.  Этот метод используется, чтобы повторить линию исходного кода или принудительно выполнить запрос, чтобы продолжить в другую функцию, например.  
  
## См. также  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)
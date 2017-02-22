---
title: "IDebugProgram2::Execute | Microsoft Docs"
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
  - "IDebugProgram2::Execute"
helpviewer_keywords: 
  - "IDebugProgram2::Execute"
ms.assetid: f7205ce8-0ac6-4fcd-b6ec-b720b4fcaccf
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram2::Execute
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Продолжает выполнять эту программу от остановленного состояния.  Очищено любое предыдущее состояние выполнения \(в качестве шага\) и запуске программы при выполнении попытку.  
  
> [!NOTE]
>  Этот метод является устаревшим.  Взамен рекомендуется использовать метод [Выполнение](../../../extensibility/debugger/reference/idebugprocess3-execute.md).  
  
## Синтаксис  
  
```cpp#  
HRESULT Execute(  
   void  
);  
```  
  
```c#  
int Execute();  
```  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Когда пользователь запускает выполнение из остановленного состояния в потоке какой\-либо другой программы, этот метод вызывается в этой программе.  Этот метод также вызывается, когда пользователь выбирает **Запуск** команда из  **Отладка** меню " в интегрированной среде разработки.  Реализация этого метода может быть как простой как вызов [Возобновить](../../../extensibility/debugger/reference/idebugthread2-resume.md) метод на текущем потоке в программе.  
  
> [!WARNING]
>  Не отправить событие остановки или немедленно \(синхронный\), событие [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) хотя обработка этого вызова; в противном случае он может повиснуть.  
  
## См. также  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)   
 [Возобновить](../../../extensibility/debugger/reference/idebugthread2-resume.md)
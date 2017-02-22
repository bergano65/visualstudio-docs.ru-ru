---
title: "IDebugProgram2::Attach | Microsoft Docs"
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
  - "IDebugProgram2::Attach"
helpviewer_keywords: 
  - "IDebugProgram2::Attach"
ms.assetid: de069fbf-a565-4905-b102-f5658c55aacd
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram2::Attach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Вложение в программе.  
  
## Синтаксис  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback  
);  
```  
  
```c#  
int Attach(   
   IDebugEventCallback2 pCallback  
);  
```  
  
#### Параметры  
 `pCallback`  
 \[in\] IDebugEventCallback2 объект, который необходимо использовать для отладки уведомление о событии.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  В следующей таблице перечислены некоторые возможные коды ошибок.  
  
|Значение|Описание|  
|--------------|--------------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Указанная программу уже вложенна в отладчике.|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Произошло нарушение безопасности при выполнении процедуры вложить.|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Программа рабочего стола нельзя вложить в отладчике.|  
  
## Заметки  
 Отладчик \(DE\) никогда не вызывает этот метод, чтобы вложить в программе.  Если DE выполняется в адресном пространстве программы, [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) вызывается метод.  Если выполнить DE в сеансе отладки адресное пространство диспетчера \(SDM\) [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md) вызывается метод.  
  
## См. также  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Attach](../../../extensibility/debugger/reference/idebugengine2-attach.md)
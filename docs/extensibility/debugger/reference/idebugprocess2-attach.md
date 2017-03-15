---
title: "IDebugProcess2::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess2::Attach"
helpviewer_keywords: 
  - "IDebugProcess2::Attach"
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProcess2::Attach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Вложение сеанс отладки \(SDM\) диспетчер к процессу.  
  
## Синтаксис  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   GUID*                 rgguidSpecificEngines,  
   DWORD                 celtSpecificEngines,  
   HRESULT*              rghrEngineAttach  
);  
```  
  
```c#  
int Attach(   
   IDebugEventCallback2 pCallback,  
   Guid[]               rgguidSpecificEngines,  
   uint                 celtSpecificEngines,  
   int[]                rghrEngineAttach  
);  
```  
  
#### Параметры  
 `pCallback`  
 \[in\] IDebugEventCallback2 объект которого используется для отладки уведомление о событии.  
  
 `rgguidSpecificEngines`  
 \[in\] массив идентификаторов GUID отладочные обработчики для отладки программы, работающие в процессе.  Этот параметр может иметь значение NULL.  Дополнительные сведения см. в разделе " примечания ".  
  
 `celtSpecificEngines`  
 \[in\] число обработчиков отладки в `rgguidSpecificEngines` массив и размер  `rghrEngineAttach` массив.  
  
 `rghrEngineAttach`  
 \[in, out\] массив кодов HRESULT, возвращаемого командами отладки.  Размер массива определяется в `celtSpecificEngines` параметр.  Как правило, то каждый код `S_OK` OR  `S_ATTACH_DEFERRED`.  Вторая показывает, что DE вложен в данный момент нет программы.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  В следующей таблице приведены другие возможные значения.  
  
|Значение|Описание|  
|--------------|--------------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Указанный процесс уже вложен в отладчике.|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Произошло нарушение безопасности при выполнении процедуры вложить.|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Процесс рабочего стола нельзя вложить в отладчике.|  
  
## Заметки  
 Вложение в процесс вложение SDM все программы, работающие в этом процессе, который может быть отлажен командами отладки \(DE\), определенными в `rgguidSpecificEngines` массив.  Установка `rgguidSpecificEngines` параметр значение NULL или включает  `GUID_NULL` в массиве, который требуется вложить все программы в процессе.  
  
 Все отладочные события, возникающие в процессе отправляются с заданным IDebugEventCallback2 объект.  This `IDebugEventCallback2` объект, предоставляемый, когда SDM вызывает этот метод.  
  
## См. также  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
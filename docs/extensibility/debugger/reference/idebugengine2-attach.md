---
title: "IDebugEngine2::Attach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2::Attach"
helpviewer_keywords: 
  - "IDebugEngine2::Attach"
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugEngine2::Attach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Вложение обработчика отладки \(DE\) для программы или все программы.  Вызывается сеанса отладки \(SDM\), если диспетчер DE выполнение внутрипроцессный к SDM.  
  
## Синтаксис  
  
```cpp#  
HRESULT Attach(   
   IDebugProgram2**      pProgram,  
   IDebugProgramNode2**  rgpProgramNodes,  
   DWORD                 celtPrograms,  
   IDebugEventCallback2* pCallback,  
   ATTACH_REASON         dwReason  
);  
```  
  
```c#  
int Attach(   
   IDebugProgram2[]     pProgram,  
   IDebugProgramNode2[] rgpProgramNodes,  
   uint                 celtPrograms,  
   IDebugEventCallback2 pCallback,  
   Enum_ATTACH_REASON   dwReason  
);  
```  
  
#### Параметры  
 `pProgram`  
 \[in\] массив IDebugProgram2 объекты, которые представляют программы, который требуется вложить.  Эти программы порта.  
  
 `rgpProgramNodes`  
 \[in\] массив IDebugProgramNode2 объекты, представляющие узлы программы, по одному для каждой программы.  Узлы программы в этом массиве представляют одни и те же программы как в выражениях `pProgram`.  Узлы программы предоставляются, так что DE мог указать программы, чтобы вложить.  
  
 `celtPrograms`  
 \[in\] количество узлов в программ или программ `pProgram` и  `rgpProgramNodes` массивы.  
  
 `pCallback`  
 \[in\] IDebugEventCallback2 объект, который будет использоваться отправлять отладочные события в SDM.  
  
 `dwReason`  
 \[in\] значение из [ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md) перечисление, указывающее причину вложить эти программы.  Дополнительные сведения см. в разделе "Замечания".  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 3 Причины вложить в программе, следующим образом:  
  
-   `ATTACH_REASON_LAUNCH` указывает, что DE вложение в программе, поскольку пользователь был запущен процесс, содержащий данный элемент.  
  
-   `ATTACH_REASON_USER` указывает, что пользователь имеет явно запрашивается DE, чтобы вложить в программе \(или процесс, содержащий программы\).  
  
-   `ATTACH_REASON_AUTO` указывает, что DE вложение в указанную программе, поскольку он уже отладки других программ в указанном процессе.  Это также называется автоматическ\-вложит.  
  
 При вызове этого метода DE отправлять такие события в последовательности:  
  
1.  [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) \(если он еще не был отправлен для указанного экземпляра ядра отладки\)  
  
2.  [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
  
3.  [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)  
  
 Кроме того, если причина вложить `ATTACH_REASON_LAUNCH`чтобы отправить, DE  [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) событие.  
  
 Как только получает DE IDebugProgramNode2 объект, соответствующий отлаживаемой программы, его можно запросить для любого закрытого интерфейса.  
  
 Перед вызовом методов узла в массиве заданной by `pProgram` OR  `rgpProgramNodes`олицетворение, при необходимости, должно быть включено на  `IDebugProgram2` интерфейс, представляющий узел программы.  Как правило, однако этот шаг не является обязательным.  Дополнительные сведения см. в разделе [Проблемы безопасности](../../../extensibility/debugger/security-issues.md).  
  
## См. также  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)
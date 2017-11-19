---
title: "IDebugEngine2::Attach | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugEngine2::Attach
helpviewer_keywords: IDebugEngine2::Attach
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7c31e4c8367c1ceba5a4692438e8c1f1503f4f63
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugengine2attach"></a>IDebugEngine2::Attach
Присоединяет отладчик (DE) к программе или программ. Вызывается диспетчером сеанса отладки (SDM) при выполняется в процессе для SDM DE.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Attach(   
   IDebugProgram2**      pProgram,  
   IDebugProgramNode2**  rgpProgramNodes,  
   DWORD                 celtPrograms,  
   IDebugEventCallback2* pCallback,  
   ATTACH_REASON         dwReason  
);  
```  
  
```csharp  
int Attach(   
   IDebugProgram2[]     pProgram,  
   IDebugProgramNode2[] rgpProgramNodes,  
   uint                 celtPrograms,  
   IDebugEventCallback2 pCallback,  
   Enum_ATTACH_REASON   dwReason  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pProgram`  
 [in] Массив [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) объекты, представляющие программы для подключения к. Это порт программы.  
  
 `rgpProgramNodes`  
 [in] Массив [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) объекты, представляющие программы узлов, по одному для каждой программы. Программа узлы в этом массиве представляют и те же программы, как и в `pProgram`. Узлы программы, получают, DE позволяет определить программы для присоединения.  
  
 `celtPrograms`  
 [in] Количество программ и узлах программы `pProgram` и `rgpProgramNodes` массивов.  
  
 `pCallback`  
 [in] [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) объект, используемый для отправки событий отладки SDM.  
  
 `dwReason`  
 [in] Значение из [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) перечисления, которое указывает причину для присоединения этих программ. Дополнительные сведения см. в разделе "Примечания".  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Существуют три причины для присоединения к программе, следующим образом:  
  
-   `ATTACH_REASON_LAUNCH`Указывает, что DE подключение к программе, поскольку пользователь запустил процесс, который содержит этот.  
  
-   `ATTACH_REASON_USER`Указывает, что пользователь явно запросил DE для присоединения к программе (или процесс, содержащий программы).  
  
-   `ATTACH_REASON_AUTO`Указывает, что DE присоединение к конкретной программе, так как он уже отладки других программ, в определенном процессе. Это также называется автоматического присоединения.  
  
 При вызове этого метода DE должен отправить эти события в последовательности:  
  
1.  [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) (если он не уже было отправлено в определенном экземпляре модуль отладки)  
  
2.  [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
  
3.  [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)  
  
 Кроме того, если присоединение причина заключается в `ATTACH_REASON_LAUNCH`, необходимо отправить DE [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) событий.  
  
 Один раз получает DE [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) объекта соответствующее отлаживаемой программы могут запрашиваться для любой закрытый интерфейс.  
  
 Перед вызовом методов, программа узла в массиве, предоставленном `pProgram` или `rgpProgramNodes`, олицетворение, при необходимости, необходимо включить функцию `IDebugProgram2` интерфейс, представляющий узел программы. Как правило тем не менее, этот шаг необязателен. Дополнительные сведения см. в разделе [проблемы безопасности](../../../extensibility/debugger/security-issues.md).  
  
## <a name="see-also"></a>См. также  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)
---
title: IDebugEngine2::Attach | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEngine2::Attach
helpviewer_keywords:
- IDebugEngine2::Attach
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9d08ceb5db30b23d9e8df77bec12c0f9cb1c2c77
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53854247"
---
# <a name="idebugengine2attach"></a>IDebugEngine2::Attach
Присоединяет отладчик (DE) к программе или программы. Вызывается диспетчером сеанса отладки (SDM), в то время когда DE выполняется в процессе для SDM.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Attach(   
   IDebugProgram2**      pProgram,  
   IDebugProgramNode2**  rgpProgramNodes,  
   DWORD                 celtPrograms,  
   IDebugEventCallback2* pCallback,  
   ATTACH_REASON         dwReason  
);  
```  
  
```csharp  
int Attach(   
   IDebugProgram2[]     pProgram,  
   IDebugProgramNode2[] rgpProgramNodes,  
   uint                 celtPrograms,  
   IDebugEventCallback2 pCallback,  
   Enum_ATTACH_REASON   dwReason  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pProgram`  
 [in] Массив [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) объекты, представляющие программы должны быть присоединены к. Это порт программы.  
  
 `rgpProgramNodes`  
 [in] Массив [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) объекты, представляющие программы узлов, по одному для каждой программы. Узлы программы в этом массиве представляют же программы, как показано на `pProgram`. Узлы программы предоставляется таким образом, DE может распознавать программы, чтобы присоединить.  
  
 `celtPrograms`  
 [in] Количество программ и узлах программы `pProgram` и `rgpProgramNodes` массивов.  
  
 `pCallback`  
 [in] [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) объект, используемый для отправки событий отладки SDM.  
  
 `dwReason`  
 [in] Значение из [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) перечисления, которое указывает причину для присоединения этих программ. Дополнительные сведения см. в разделе "Примечания".  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Существуют три причины для присоединения к программе, следующим образом:  
  
- `ATTACH_REASON_LAUNCH` Указывает, что DE присоединяется к программы, так как пользователь запустит процесс, который его содержит.  
  
- `ATTACH_REASON_USER` Указывает, что пользователь явно запросил DE для присоединения к программе (или процесс, который содержит программу).  
  
- `ATTACH_REASON_AUTO` Указывает, что DE присоединяется к конкретной программы, так как он уже отладки других программ в определенном процессе. Это также называется автоматического присоединения.  
  
  При вызове этого метода, DE должен отправить эти события в последовательности:  
  
1. [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) (если он не уже был отправлен для конкретного экземпляра модуля отладки)  
  
2. [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
  
3. [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)  
  
   Кроме того, если присоединение связано `ATTACH_REASON_LAUNCH`, DE должен отправить [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) событий.  
  
   Приведенный ниже код один раз получает DE [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) объект, соответствующий отлаживаемой программы могут запрашиваться для любого частного интерфейса.  
  
   Перед вызовом методов, программа узла в массиве, выданный `pProgram` или `rgpProgramNodes`, олицетворение, при необходимости, должен быть включен на `IDebugProgram2` интерфейс, представляющий узел программы. Как правило тем не менее, этот шаг необязателен. Дополнительные сведения см. в разделе [проблемы безопасности](../../../extensibility/debugger/security-issues.md).  
  
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
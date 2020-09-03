---
title: 'IDebugEngine2:: Attach | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine2::Attach
helpviewer_keywords:
- IDebugEngine2::Attach
ms.assetid: 173dcbda-5019-4c5e-bca9-a071838b5739
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a82d26fbfd6fe08f4976aaa7643bcaa95008032f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196046"
---
# <a name="idebugengine2attach"></a>IDebugEngine2::Attach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Присоединяет модуль отладки (DE) к программе или программам. Вызывается диспетчером отладки сеанса (SDM), когда DE выполняется в процессе в SDM.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 окне Массив объектов [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) , представляющих программы, к которым следует присоединиться. Это программы порта.  
  
 `rgpProgramNodes`  
 окне Массив объектов [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) , представляющих узлы программы, по одному для каждой программы. Узлы программы в этом массиве представляют те же программы, что и в `pProgram` . Узлы программы предоставляются таким образом, чтобы программа DE могла определить программы, к которым следует присоединиться.  
  
 `celtPrograms`  
 окне Количество программ и/или узлов программ в `pProgram` `rgpProgramNodes` массивах и.  
  
 `pCallback`  
 окне Объект [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , который будет использоваться для отправки событий отладки в SDM.  
  
 `dwReason`  
 окне Значение из перечисления [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) , указывающее причину присоединения этих программ. Дополнительные сведения см. в разделе "Примечания".  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Существует три причины присоединения к программе следующим образом.  
  
- `ATTACH_REASON_LAUNCH` Указывает, что DE присоединяется к программе, так как пользователь запускает процесс, который его содержит.  
  
- `ATTACH_REASON_USER` Указывает, что пользователь явным образом запросил соединение DE к программе (или процессу, содержащему программу).  
  
- `ATTACH_REASON_AUTO` Указывает, что DE присоединяется к определенной программе, поскольку уже выполняется отладка других программ в определенном процессе. Это также называется присоединением.  
  
  При вызове этого метода метод DE должен отправить эти события последовательно:  
  
1. [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) (если он еще не был отправлен для конкретного экземпляра модуля отладки)  
  
2. [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)  
  
3. [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)  
  
   Кроме того, если причиной присоединения является `ATTACH_REASON_LAUNCH` , то de должен отправить событие [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) .  
  
   После того, как программа DE получает объект [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) , соответствующий отлаживаемой программе, она может быть запрошена для любого частного интерфейса.  
  
   Перед вызовом методов узла программы в массиве, заданном параметром `pProgram` или `rgpProgramNodes` , необходимо включить олицетворение (при необходимости) для `IDebugProgram2` интерфейса, представляющего узел программы. Однако обычно этот шаг не требуется. Дополнительные сведения см. в разделе [вопросы безопасности](../../../extensibility/debugger/security-issues.md).  
  
## <a name="see-also"></a>См. также:  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md)   
 [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)   
 [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)   
 [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md)   
 [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md)

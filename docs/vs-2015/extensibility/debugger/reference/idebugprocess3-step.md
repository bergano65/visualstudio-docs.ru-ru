---
title: IDebugProcess3::Step | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess3::Step
helpviewer_keywords:
- IDebugProcess3::Step
ms.assetid: 6ad9094c-27cc-4927-8a7c-1b4d97b2e436
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 367f775cdf8ade1db41bbb05cd4ca9c424496e9a
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58993068"
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Вызывает процесс, чтобы шаг одну инструкцию или инструкции.  
  
> [!NOTE]
>  Этот метод следует использовать вместо [шаг](../../../extensibility/debugger/reference/idebugprogram2-step.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Step(  
   IDebugThread2* pThread,  
   STEPKIND       sk,  
   STEPUNIT       step,  
);  
```  
  
```csharp  
int Step(  
   IDebugThread2 pThread,   
   enum_STEPKIND sk,   
   enum_STEPUNIT step  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pThread`  
 [in] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) объект, представляющий поток, в настоящее время шаг.  
  
 `sk`  
 [in] Один из [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) значения.  
  
 `step`  
 [in] Один из [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) значения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 В случае любой синхронизации потоков или связи между потоками, другие потоки в процессе следует запускать при отладке определенного потока.  
  
 **Предупреждение** событии остановки или немедленно (синхронно) событие, чтобы не отправлять [событий](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) при обработке этого вызова; в противном случае отладчик может зависнуть.  
  
## <a name="see-also"></a>См. также  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [STEPKIND](../../../extensibility/debugger/reference/stepkind.md)   
 [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)

---
title: IDebugProgram2::Step | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 861c9ba2c6266294f5da9f6cd03ea9e85971e07d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53950463"
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
Выполняет шаг.  
  
> [!NOTE]
>  Этот метод является устаревшим. Используйте [шаг](../../../extensibility/debugger/reference/idebugprocess3-step.md) метод вместо этого.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Step(   
   IDebugThread2*  pThread,  
   STEPKIND        sk,  
   STEPUNIT        step  
);  
```  
  
```csharp  
int Step(   
   IDebugThread2  pThread,  
   enum_STEPKIND  sk,  
   enum_STEPUNIT  step  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pThread`  
 [in] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , представляющий поток, в настоящее время шаг.  
  
 `sk`  
 [in] Значение из [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) перечисление, указывающее тип шага.  
  
 `step`  
 [in] Значение из [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) перечисление, указывающее единицы шага (например, путем инструкцию или инструкции).  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 В случае любой синхронизации потоков или связи между потоками, другие потоки в программе следует запускать при отладке определенного потока.  
  
> [!WARNING]
>  В случае остановки или немедленно (синхронно) событие, чтобы не отправлять [событий](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) при обработке этого вызова; в противном случае отладчик может зависнуть.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
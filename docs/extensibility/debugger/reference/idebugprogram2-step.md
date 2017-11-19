---
title: "IDebugProgram2::Step | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::Step
helpviewer_keywords: IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d0e4b8533c1b6a14c61fc556f06594945037bbbd
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
Выполняет шаг.  
  
> [!NOTE]
>  Этот метод является устаревшим. Используйте [шаг](../../../extensibility/debugger/reference/idebugprocess3-step.md) метод вместо него.  
  
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
 [in] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , представляющий поток, который в настоящее время шаг.  
  
 `sk`  
 [in] Значение из [STEPKIND](../../../extensibility/debugger/reference/stepkind.md) перечисление, указывающее тип шага.  
  
 `step`  
 [in] Значение из [STEPUNIT](../../../extensibility/debugger/reference/stepunit.md) перечисления, которое указывает единицу шага (например, инструкциями или инструкции).  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 В случае любой синхронизации потоков или связи между потоками, другие потоки в программе следует запускать при отладке определенного потока.  
  
> [!WARNING]
>  Не отправлять события остановки или немедленно (синхронно) событие [событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) при обработке этого вызова; в противном случае отладчик может зависнуть.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
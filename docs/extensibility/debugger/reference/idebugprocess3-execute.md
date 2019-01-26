---
title: IDebugProcess3::Execute | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProcess3::Execute
helpviewer_keywords:
- IDebugProcess3::Execute
ms.assetid: d831cd81-d7bf-4172-8517-aa699867791f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 160551eed2111d5e92a5fef6b47e305ab7709a74
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54962917"
---
# <a name="idebugprocess3execute"></a>IDebugProcess3::Execute
По-прежнему запускать этот процесс в остановленном состоянии. Очистить все предыдущие состояния выполнения (например, шаг), и процесс начинается снова выполните.  
  
> [!NOTE]
>  Этот метод следует использовать вместо [Execute](../../../extensibility/debugger/reference/idebugprogram2-execute.md).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Execute(  
   IDebugThread2* pThread  
);  
```  
  
```csharp  
int Execute(  
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pThread`  
 [in] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) объект, представляющий выполнение потока.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Когда пользователь начинает выполнение в остановленном состоянии, в какой-либо другой процесс потока, этот метод вызывается об этом процессе. Этот метод также вызывается, когда пользователь выбирает **запустить** команду **Отладка** меню в интегрированной среде разработки. Реализация этого метода может быть простым вызовом [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) метода в текущем потоке в процессе.  
  
> [!WARNING]
>  В случае остановки или немедленно (синхронно) событие, чтобы не отправлять [событий](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) при обработке этого вызова; в противном случае отладчик может зависнуть.  
  
## <a name="see-also"></a>См. также  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Резюме](../../../extensibility/debugger/reference/idebugthread2-resume.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
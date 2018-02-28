---
title: "IDebugProgram2::Continue | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgram2::Continue
helpviewer_keywords:
- IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 5c90c456c4825ea9da054f7e78621493cc90a648
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
Продолжает выполнение программы в остановленном состоянии. Предыдущее состояние выполнения (например, шаг) сохраняются, и программа начинает выполнение еще раз.  
  
> [!NOTE]
>  Этот метод является устаревшим. Используйте [Продолжить](../../../extensibility/debugger/reference/idebugprocess3-continue.md) метод вместо него.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Continue(   
   IDebugThread2* pThread  
);  
```  
  
```csharp  
int Continue(   
   IDebugThread2 pThread  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pThread`  
 [in] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , представляющий поток.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод вызывается для данной программы, независимо от того, сколько программ отлаживаемых или программу, которая создается событие остановки. Реализация должна сохраняют предыдущее состояние выполнения (например, шаг) и продолжить выполнение, как будто он никогда не остановился до завершения предыдущего выполнения. То есть если потока в этой программе выполняло операции обход и была остановлена, поскольку другой программы остановлена, а затем этот метод был вызван, программа необходимо выполнить исходную операцию обход.  
  
> [!WARNING]
>  Не отправлять события остановки или немедленно (синхронно) событие [событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) при обработке этого вызова; в противном случае отладчик может зависнуть.  
  
## <a name="see-also"></a>См. также  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
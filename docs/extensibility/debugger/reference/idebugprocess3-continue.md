---
title: "IDebugProcess3::Continue | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProcess3::Continue
helpviewer_keywords:
- IDebugProcess3::Continue
ms.assetid: 57506242-5763-4c08-adb9-8a78ce02cebb
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: f666f35a71f65b839073e7d360bc357627fb7c5f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocess3continue"></a>IDebugProcess3::Continue
По-прежнему запускать этот процесс в остановленном состоянии. Предыдущее состояние выполнения (например, шаг) сохраняются, и процесс начинается выполнение еще раз.  
  
> [!NOTE]
>  Этот метод следует использовать вместо [Продолжить](../../../extensibility/debugger/reference/idebugprogram2-continue.md).  
  
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
 [in] [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) объект, представляющий поток будет продолжен.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод вызывается для независимо от отлаживаемых процессов, сколько или процесса, в котором создается событие остановки этого процесса. Реализация должна сохраняют предыдущее состояние выполнения (например, шаг) и продолжить выполнение, как будто он никогда не остановился до завершения предыдущего выполнения. То есть, если поток в этот процесс выполняло операции обход и была остановлена из-за остановки занято другим процессом, а затем `Continue` был вызван, указанный поток должен завершить исходную операцию обход.  
  
 **Предупреждение** не отправляют событие остановки или немедленно (синхронно) событие [событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) при обработке этого вызова; в противном случае отладчик может зависнуть.  
  
## <a name="see-also"></a>См. также  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)
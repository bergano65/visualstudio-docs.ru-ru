---
title: IDebugProgram2::Continue | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugProgram2::Continue
helpviewer_keywords:
- IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d787e06c2586a2d5c3b6c48817262c80e14183d2
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49825344"
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Продолжает выполнение программы в остановленном состоянии. Сохраняется все предыдущие состояния выполнения (например, шаг), и начнется снова выполнение программы.  
  
> [!NOTE]
>  Этот метод является устаревшим. Используйте [Продолжить](../../../extensibility/debugger/reference/idebugprocess3-continue.md) метод вместо этого.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод вызывается для данной программы, независимо от того, сколько программ отлаживаемых или какая программа создала событие stopping. Реализация должна сохранить предыдущее состояние выполнения (например, шаг) и продолжить выполнение, как будто его никогда не было остановлено до завершения предыдущего выполнения. То есть если поток в этой программе выполнялась операция обходе, а была прервана, поскольку другой программы остановлена, а затем этот метод был вызван, программы необходимо выполнить исходной операции обходе.  
  
> [!WARNING]
>  В случае остановки или немедленно (синхронно) событие, чтобы не отправлять [событий](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) при обработке этого вызова; в противном случае отладчик может зависнуть.  
  
## <a name="see-also"></a>См. также  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Event](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)


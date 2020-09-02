---
title: 'IDebugProgram2:: Continue | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::Continue
helpviewer_keywords:
- IDebugProgram2::Continue
ms.assetid: e5a6e02a-d21b-4a03-a034-e8de1f71ce2e
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 461aa702350e1385e01df6f78e942bbe73b16402
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "86386203"
---
# <a name="idebugprogram2continue"></a>IDebugProgram2::Continue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Продолжение выполнения этой программы из остановленного состояния. Все предыдущие состояния выполнения (например, шаг) сохраняются, и программа начинает выполнение повторно.  
  
> [!NOTE]
> Этот метод является устаревшим. Вместо этого используйте метод [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) .  
  
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
 окне Объект [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , представляющий поток.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Этот метод вызывается для этой программы независимо от количества отлаживаемых программ или от программы, создавшей событие остановки. Реализация должна сохранить предыдущее состояние выполнения (например, шаг) и продолжить выполнение, как будто оно никогда не было остановлено до завершения предыдущего выполнения. То есть, если поток в этой программе выполнял операцию поэтапного выполнения и был остановлен из-за остановки какой-либо другой программы, а затем был вызван этот метод, программа должна выполнить исходную операцию пошагового выполнения.  
  
> [!WARNING]
> Не отправляйте событие остановки или мгновенное (синхронное) событие в [событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) при обработке этого вызова; в противном случае отладчик может перестать отвечать на запросы.  
  
## <a name="see-also"></a>См. также:  
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)

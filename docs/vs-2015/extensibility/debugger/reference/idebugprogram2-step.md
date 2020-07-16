---
title: 'IDebugProgram2:: шаг | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::Step
helpviewer_keywords:
- IDebugProgram2::Step
ms.assetid: e4c2ffce-9810-4088-8162-eac9ef04f2a9
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dd9d314865eb2051b67d7c127a6c5cc2395b1863
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2020
ms.locfileid: "86387230"
---
# <a name="idebugprogram2step"></a>IDebugProgram2::Step
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Выполняет шаг.  
  
> [!NOTE]
> Этот метод является устаревшим. Вместо этого используйте метод [Step](../../../extensibility/debugger/reference/idebugprocess3-step.md) .  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 окне Объект [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , представляющий поток, для которого выполняется пошаговое выполнение.  
  
 `sk`  
 окне Значение из перечисления [степкинд](../../../extensibility/debugger/reference/stepkind.md) , указывающее тип шага.  
  
 `step`  
 окне Значение из перечисления [степунит](../../../extensibility/debugger/reference/stepunit.md) , которое указывает единицу шага (например, инструкцию или инструкцию).  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Если существует любая синхронизация потоков или обмен данными между потоками, другие потоки в программе должны выполняться, когда конкретный поток пошаговым выполнением.  
  
> [!WARNING]
> Не отправляйте событие остановки или мгновенное (синхронное) событие в [событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) при обработке этого вызова; в противном случае отладчик может перестать отвечать на запросы.  
  
## <a name="see-also"></a>См. также:  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)   
 [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)

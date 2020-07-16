---
title: 'IDebugProcess3:: шаг | Документация Майкрософт'
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
ms.openlocfilehash: 5069a40f4e3ea4b1fba74c8133a18b46f2b3f2d2
ms.sourcegitcommit: a77158415da04e9bb8b33c332f6cca8f14c08f8c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/15/2020
ms.locfileid: "86386229"
---
# <a name="idebugprocess3step"></a>IDebugProcess3::Step
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Заставляет процесс выполнить шаг 1 инструкции или инструкции.  
  
> [!NOTE]
> Этот метод следует использовать вместо [шага](../../../extensibility/debugger/reference/idebugprogram2-step.md).  
  
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
 окне Объект [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , представляющий поток, для которого выполняется пошаговое выполнение.  
  
 `sk`  
 окне Одно из значений [степкинд](../../../extensibility/debugger/reference/stepkind.md) .  
  
 `step`  
 окне Одно из значений [степунит](../../../extensibility/debugger/reference/stepunit.md) .  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Если существует какая-либо синхронизация потоков или обмен данными между потоками, другие потоки в процессе будут выполняться, когда конкретный поток пошаговым выполнением.  
  
 **Предупреждение об ошибке** Не отправляйте событие остановки или мгновенное (синхронное) событие в [событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md) при обработке этого вызова; в противном случае отладчик может перестать отвечать на запросы.  
  
## <a name="see-also"></a>См. также:  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [степкинд](../../../extensibility/debugger/reference/stepkind.md)   
 [степунит](../../../extensibility/debugger/reference/stepunit.md)   
 [Событие](../../../extensibility/debugger/reference/idebugeventcallback2-event.md)

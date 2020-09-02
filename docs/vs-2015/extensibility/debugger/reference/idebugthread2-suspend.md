---
title: 'IDebugThread2:: Suspend | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugThread2::Suspend
helpviewer_keywords:
- IDebugThread2::Suspend
ms.assetid: 1e20be85-aa12-48de-bb83-0bf0976e99ae
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c334a660b9c85345c636c7cc4b9aaea1a9b12076
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152951"
---
# <a name="idebugthread2suspend"></a>IDebugThread2::Suspend
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Приостанавливает поток.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Suspend (   
   DWORD *pdwSuspendCount  
);  
```  
  
```csharp  
HRESULT Suspend (   
   out uint pdwSuspendCount  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdwSuspendCount`  
 заполняет Возвращает счетчик приостановок после операции приостановки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Каждый вызов этого метода увеличивает значение счетчика приостановки выше 0. Это число приостановок отображается в окне отладки **потоков** .  
  
 Для каждого вызова этого метода должен быть последующий вызов метода [Resume](../../../extensibility/debugger/reference/idebugthread2-resume.md) .  
  
## <a name="see-also"></a>См. также:  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Возобновить](../../../extensibility/debugger/reference/idebugthread2-resume.md)

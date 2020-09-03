---
title: 'IDebugThread2:: Resume | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5bdec7338864926187b3d5056ffd2f2c4e1d7824
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152996"
---
# <a name="idebugthread2resume"></a>IDebugThread2::Resume
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возобновляет выполнение потока.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Resume (   
   DWORD *pdwSuspendCount  
);  
```  
  
```csharp  
int Resume (   
   out uint pdwSuspendCount  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdwSuspendCount`  
 заполняет Возвращает счетчик приостановок после операции возобновления.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Каждый вызов этого метода уменьшает число приостановок до тех пор, пока не достигнет значения 0, после чего выполнение фактически возобновляется. Это число приостановок отображается в окне отладки **потоков** .  
  
 Для каждого вызова этого метода должен быть предыдущий вызов метода [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md) . Счетчик приостановов определяет, сколько раз `IDebugThread2::Suspend` был вызван метод.  
  
## <a name="see-also"></a>См. также:  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Приостановить](../../../extensibility/debugger/reference/idebugthread2-suspend.md)

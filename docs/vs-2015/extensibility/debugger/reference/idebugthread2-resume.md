---
title: IDebugThread2::Resume | Документация Майкрософт
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
- IDebugThread2::Resume
helpviewer_keywords:
- IDebugThread2::Resume
ms.assetid: 36aad682-b0b9-40a2-b3fc-f0e61d41cdbc
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c4ac56cd7763fa8fe3ee1326a83efd33f5f2a396
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49214491"
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
 [out] Возвращает счетчик приостановок после операции возобновления.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 При каждом вызове этого метода уменьшает счетчик приостановок возобновляется пока не достигнет 0 в это время выполнения. Этот счетчик приостановок отображается в **потоков** окно отладки.  
  
 Для каждого вызова этого метода, должно существовать предыдущего вызова [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md) метод. Счетчик приостановок определяет, сколько раз `IDebugThread2::Suspend` моменту вызова метода.  
  
## <a name="see-also"></a>См. также  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [Suspend](../../../extensibility/debugger/reference/idebugthread2-suspend.md)


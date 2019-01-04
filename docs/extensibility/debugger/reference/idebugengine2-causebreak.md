---
title: IDebugEngine2::CauseBreak | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEngine2::CauseBreak
helpviewer_keywords:
- IDebugEngine2::CauseBreak
ms.assetid: 17fe4698-b04e-4798-8412-80e0da60c387
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1d0c3862468d5ad1a9c548297a69d9ae10521e59
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53964381"
---
# <a name="idebugengine2causebreak"></a>IDebugEngine2::CauseBreak
Запросы, что все программы, отлаживаемой, этот модуль отладки (DE), чтобы остановить выполнение следующего, один из своих потоков пытается выполнить.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT CauseBreak(   
   void   
);  
```  
  
```csharp  
int CauseBreak();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод является асинхронным: [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) событие отправляется, когда программа затем пытается выполнить после вызова этого метода.  
  
## <a name="see-also"></a>См. также  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
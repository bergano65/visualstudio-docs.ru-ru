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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7a27d0dd5c501076f7ee2354736b989a441395df
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54954960"
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
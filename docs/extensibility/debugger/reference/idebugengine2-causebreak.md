---
title: IDebugEngine2::CauseBreak | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 2ba10e167246ce2467f2faebf157e46306749bdb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31105214"
---
# <a name="idebugengine2causebreak"></a>IDebugEngine2::CauseBreak
Все программы, отлаживаемой этого подсистема отладки (DE), чтобы остановить выполнение следующей запросов, один из своих потоков попытается запустить.  
  
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
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод является асинхронным: [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) событие отправляется, когда программа затем пытается выполнить после вызова этого метода.  
  
## <a name="see-also"></a>См. также  
 [CauseBreak](../../../extensibility/debugger/reference/idebugprogram2-causebreak.md)   
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
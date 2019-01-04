---
title: IDebugProcess2::CauseBreak | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProcess2::CauseBreak
helpviewer_keywords:
- IDebugProcess2::CauseBreak
ms.assetid: efda8865-2319-4d53-90bf-6d9d74cd5195
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 7a52a360773443b1b179ad3cdec91f3924cedc9a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53923024"
---
# <a name="idebugprocess2causebreak"></a>IDebugProcess2::CauseBreak
Запросы, что следующий программу, которая выполнение кода в этом процессе halt и отправить [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) объект события.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT CauseBreak(   
   void  
);  
```  
  
```csharp  
int CauseBreak();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
---
title: IDebugProgram2::CauseBreak | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugProgram2::CauseBreak
helpviewer_keywords:
- IDebugProgram2::CauseBreak
ms.assetid: 07d353fc-68ab-4297-a18f-3d3c7a80e121
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1f7dbad02632663474f62f561773aa62a8735071
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/26/2019
ms.locfileid: "55069386"
---
# <a name="idebugprogram2causebreak"></a>IDebugProgram2::CauseBreak
Запрашивает, чтобы программа остановил выполнение следующего время один из потоков попыток запуска.  
  
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
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) событий отправляется в том случае, когда программа попытается Далее для выполнения кода после вызова этого метода.  
  
 Этот метод является асинхронным, в том, что метод немедленно возвращается, не обязательно ожидании остановку программы.  
  
## <a name="see-also"></a>См. также  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md)
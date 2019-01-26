---
title: IDebugFunctionObject2::Evaluate | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugFunctionObject2::Evaluate
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bab355371d26b59ff078798aea205102821e1f0a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55043262"
---
# <a name="idebugfunctionobject2evaluate"></a>IDebugFunctionObject2::Evaluate
Вызывает функцию и возвращает результирующее значение как объект.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Evaluate (  
   IDebugObject** ppParams,  
   DWORD          dwParams,  
   DWORD          dwEvalFlags,  
   DWORD          dwTimeout,  
   IDebugObject** ppResult  
);  
```  
  
```csharp  
int Evaluate (  
   IDebugObject     ppParams,  
   uint             dwParams,  
   uint             dwEvalFlags,  
   uint             dwTimeout,  
   out IDebugObject ppResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppParams`  
 [in] Массив [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) объекты, которые представляют входные параметры. Каждый из этих параметров был создан с помощью одного из методов создания в этом интерфейсе.  
  
 `dwParams`  
 [in] Число параметров в `ppParams` массива.  
  
 `dwEvalFlags`  
 [in] Сочетание флагов из [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) перечисления, укажите, каким образом будет осуществляться вычисления.  
  
 `dwTimeout`  
 [in] Указывает максимальное время в миллисекундах для ожидания перед возвратом из этого метода. Используйте **БЕСКОНЕЧНЫЙ** для неограниченного времени ожидания.  
  
 `ppResult`  
 [out] Возвращает **IDebugObject** , представляющий значение функции в виде объекта.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
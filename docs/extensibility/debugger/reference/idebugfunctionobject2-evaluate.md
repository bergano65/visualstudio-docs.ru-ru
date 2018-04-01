---
title: IDebugFunctionObject2::Evaluate | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugFunctionObject2::Evaluate
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
caps.latest.revision: 8
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: a77b00c8c12fb355d53cff0008e41217626b6f9b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugfunctionobject2evaluate"></a>IDebugFunctionObject2::Evaluate
Вызывает функцию и возвращает результирующее значение в виде объекта.  
  
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
 [in] Массив [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) объекты, которые представляют входные параметры. Каждый из этих параметров был создан с помощью одного из методов создания в данном интерфейсе.  
  
 `dwParams`  
 [in] Число параметров в `ppParams` массива.  
  
 `dwEvalFlags`  
 [in] Сочетание флагов из [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) перечисления, укажите, как будет выполняться вычисление.  
  
 `dwTimeout`  
 [in] Указывает максимальное время (в миллисекундах) ожидания перед возвратом из этого метода. Используйте **БЕСКОНЕЧНЫЙ** неограниченное время ожидания.  
  
 `ppResult`  
 [out] Возвращает **IDebugObject** , представляющий значение функции, как объект.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
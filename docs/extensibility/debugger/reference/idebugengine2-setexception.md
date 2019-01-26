---
title: IDebugEngine2::SetException | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEngine2::SetException
helpviewer_keywords:
- IDebugEngine2::SetException
ms.assetid: e6f5ec48-09e8-4b9b-9dc9-55f8d883f1b7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e423f7817d47473111ac6eb1c5293127826c2b99
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55034327"
---
# <a name="idebugengine2setexception"></a>IDebugEngine2::SetException
Указывает, как модуль отладки (DE) должен обрабатывать данного исключения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT SetException(   
   EXCEPTION_INFO* pException  
);  
```  
  
```csharp  
int SetException(   
   EXCEPTION_INFO[] pException  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pException`  
 [in] [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) структура, описывающая исключение и как выполнить его отладку.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Чтобы остановить программу, генерации исключения в первый шанс обработки, второй вероятность того, можно было передать инструкцию DE или вообще не.  
  
## <a name="see-also"></a>См. также  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
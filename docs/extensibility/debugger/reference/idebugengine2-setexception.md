---
title: IDebugEngine2::SetException | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugEngine2::SetException
helpviewer_keywords:
- IDebugEngine2::SetException
ms.assetid: e6f5ec48-09e8-4b9b-9dc9-55f8d883f1b7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f200f02ec3a79c3ccdece3a4cc0ae5b10e2b491c
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49927604"
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
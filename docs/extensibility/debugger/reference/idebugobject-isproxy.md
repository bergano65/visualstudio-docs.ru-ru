---
title: IDebugObject::IsProxy | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugObject::IsProxy
- IsProxy
ms.assetid: 06c66b87-db95-4400-ab26-5d33e743a439
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b32fcff6a365f37c926194560674da354f0f08ee
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54918723"
---
# <a name="idebugobjectisproxy"></a>IDebugObject::IsProxy
Определяет, является ли объект прозрачный прокси-сервер.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT IsProxy (  
   BOOL* pfIsProxy  
);  
```  
  
```csharp  
int IsProxy (  
   out bool pfIsProxy  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pfIsProxy`  
 [out] `TRUE` Если объект является прозрачным прокси; в противном случае `FALSE`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод реализуется модулем отладки C++ по умолчанию.  
  
## <a name="see-also"></a>См. также  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
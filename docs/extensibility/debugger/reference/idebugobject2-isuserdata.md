---
title: IDebugObject2::IsUserData | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugObject2::IsUserData
helpviewer_keywords:
- IDebugObject2::IsUserData method
ms.assetid: 6ffa0d0e-f742-496d-acc7-db74c248bc45
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8022c5e618df682456b81bc716e0964ff2c3a94d
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53834351"
---
# <a name="idebugobject2isuserdata"></a>IDebugObject2::IsUserData
Определяет, представляет ли объект данных пользователя.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT IsUserData(  
   BOOL* pfUser  
);  
```  
  
```csharp  
int IsUserData(  
   out int pfUser  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pfUser`  
 [out] Возвращает ненулевое значение (`TRUE`), если объект представляет данные пользователя; ноль (`FALSE`) Если это не так.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Данные пользователя — это любой объект, который является частью модуля, обозначены как JustMyCode (настраивается пользователем параметр, отмечающий модуля, как пользовательский код и поэтому отображаются в трассировке стека).  
  
## <a name="see-also"></a>См. также  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
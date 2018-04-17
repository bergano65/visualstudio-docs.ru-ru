---
title: IDebugObject2::IsUserData | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 8c20b4e531284156b8790b1ca65b32c85d1db997
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugobject2isuserdata"></a>IDebugObject2::IsUserData
Определяет, представляет ли объект пользовательских данных.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT IsUserData(  
   BOOL* pfUser  
);  
```  
  
```csharp  
int IsUserData(  
   out int pfUser  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pfUser`  
 [out] Возвращает ненулевое значение (`TRUE`), если объект представляет данные пользователя; ноль (`FALSE`) Если это не так.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Данные пользователя является любой объект, который является частью модуля, в качестве JustMyCode (настраивается пользователем параметр, обозначающий модуля, как код пользователя и поэтому видимым в трассировке стека).  
  
## <a name="see-also"></a>См. также  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
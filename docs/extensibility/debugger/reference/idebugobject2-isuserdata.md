---
title: "IDebugObject2::IsUserData | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugObject2::IsUserData
helpviewer_keywords: IDebugObject2::IsUserData method
ms.assetid: 6ffa0d0e-f742-496d-acc7-db74c248bc45
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ac758e7e8ce4d288b347b1207883642c920059bb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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
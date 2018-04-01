---
title: IDebugObject::IsReadOnly | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugObject::IsReadOnly
helpviewer_keywords:
- IDebugObject::IsReadOnly method
ms.assetid: c460f772-d08a-4b36-81f3-dff6a51a93fd
caps.latest.revision: 9
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: f1bcd4dc3f23a5305a2b40ee19affb8ae28ffd6f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugobjectisreadonly"></a>IDebugObject::IsReadOnly
Определяет, является ли этот объект только для чтения.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT IsReadOnly(   
   BOOL* pfIsReadOnly  
);  
```  
  
```csharp  
int IsReadOnly(  
   out int pfIsReadOnly  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pfIsReadOnly`  
 [out] Возвращает ненулевое значение (`TRUE`) Если этот объект только для чтения; в противном случае возвращает ноль (`FALSE`).  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Объект только для чтения не может быть изменен после его создания.  
  
## <a name="see-also"></a>См. также  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
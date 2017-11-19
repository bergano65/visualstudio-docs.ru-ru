---
title: "IDebugReference2::SetReferenceType | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugReference2::SetReferenceType
helpviewer_keywords: IDebugReference2::SetReferenceType
ms.assetid: 5854a172-ea82-481c-97d9-c7fc16923d44
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1abe3627f11540f43e59d4d22cec6598a924fa3b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idebugreference2setreferencetype"></a>IDebugReference2::SetReferenceType
Задает ссылочный тип. Зарезервировано для будущего использования.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT SetReferenceType (   
   REFERENCE_TYPE dwRefType  
);  
```  
  
```csharp  
int SetReferenceType (   
   enum_REFERENCE_TYPE dwRefType  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwRefType`  
 [in] Значение из [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md) перечисления, которое указывает тип ссылки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Всегда возвращает значение `E_NOTIMPL`.  
  
## <a name="see-also"></a>См. также  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)   
 [REFERENCE_TYPE](../../../extensibility/debugger/reference/reference-type.md)
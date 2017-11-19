---
title: "IEnumDebugAddresses::GetCount | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugAddresses::GetCount
helpviewer_keywords: IEnumDebugAddresses::GetCount method
ms.assetid: f2ca8ff8-539f-457c-83f8-9bbf97618065
caps.latest.revision: "5"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e03a8c35a2e0bae6748bfe9737e8e21923390762
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugaddressesgetcount"></a>IEnumDebugAddresses::GetCount
Этот метод возвращает количество элементов в перечислении.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetCount(  
   [out] ULONG* pcelt  
);  
```  
  
```csharp  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pcelt`  
 [out] Возвращает число элементов в перечислении.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод не является частью обычной COM-интерфейс перечисления которого указывает, что только Далее, клонирования, Skip и сброса необходимо реализовать.  
  
## <a name="see-also"></a>См. также  
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
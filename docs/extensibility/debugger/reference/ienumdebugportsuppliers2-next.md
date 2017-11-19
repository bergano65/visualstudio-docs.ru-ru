---
title: "IEnumDebugPortSuppliers2::Next | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEnumDebugPortSuppliers2::Next
helpviewer_keywords: IEnumDebugPortSuppliers2::Next
ms.assetid: e2a2d226-e70b-42c2-bf00-a936517940c8
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 139edb87a285b31d267fd16f77f1962a9966b950
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="ienumdebugportsuppliers2next"></a>IEnumDebugPortSuppliers2::Next
Возвращает следующий набор элементов из перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Next(  
   ULONG                 celt,  
   IDebugPortSupplier2** rgelt,  
   ULONG*                pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint                  celt,  
   IDebugPortSupplier2[] rgelt,  
   ref uint              pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `celt`  
 [in] Число элементов для извлечения. Также указывает максимальный размер `rgelt` массива.  
  
 `rgelt`  
 [in, out] Массив [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) элементы, которые должны заполняться в.  
  
 `pceltFetched`  
 [out] Возвращает количество элементов, фактически извлеченных в `rgelt`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` меньше запрошенного числа элементов может быть возвращен; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md)   
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
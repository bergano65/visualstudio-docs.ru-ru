---
title: IEEDataStorage::GetSize | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEEDataStorage::GetSize
helpviewer_keywords:
- IEEDataStorage::GetSize
ms.assetid: 33d232c4-1239-4abc-922b-e1bc5b908169
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 64f78005e4f3f7027cb6621e67cfbe44be4af3a0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53848750"
---
# <a name="ieedatastoragegetsize"></a>IEEDataStorage::GetSize
Возвращает число байтов, содержащихся в этом объекте.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetSize(  
   ULONG* size  
);  
```  
  
```csharp  
int GetSize(  
   out uint size  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `size`  
 [out] Число байтов, содержащихся в этом объекте.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Используйте [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md) метод для извлечения фактических данных байты.  
  
## <a name="see-also"></a>См. также  
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [GetData](../../../extensibility/debugger/reference/ieedatastorage-getdata.md)
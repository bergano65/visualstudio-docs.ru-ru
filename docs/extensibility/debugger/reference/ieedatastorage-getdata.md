---
title: IEEDataStorage::GetData | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 88ca53843c342547a0c0641bcb76f8e1166723ab
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49860596"
---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
Получает указанное число байтов из объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetData(  
   ULONG  dataSize,  
   ULONG* sizeGotten,  
   BYTE*  data  
);  
```  
  
```csharp  
int GetData(  
   uint     dataSize,  
   out uint sizeGotten,  
   byte[]   data  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dataSize`  
 [in] Число байтов для получения ( `data` массива должен вмещать не менее это число байтов).  
  
 `sizeGotten`  
 [out] Возвращает число фактически извлеченных байтов.  
  
 `data`  
 [in, out] Массив, заполненный запрошенные данные.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод рекомендуется используется для получения всех байтов данных в локальный массив, поскольку нет способа для пропуска байтов в процесс извлечения. В данном случае параметр `dataSize` должно быть значение, возвращаемое функцией [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md) метод.  
  
## <a name="see-also"></a>См. также  
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)
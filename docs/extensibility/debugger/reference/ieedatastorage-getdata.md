---
title: "IEEDataStorage::GetData | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IEEDataStorage::GetData
helpviewer_keywords: IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e18b51c20d2eaf324782574bf007ce32fdc6df2e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
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
 [out] Возвращает число байтов, фактически полученных.  
  
 `data`  
 [in, out] Массив, который заполняется запрошенные данные.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод рекомендуется используется для получения всех байтов данных в локальный массив, поскольку нет возможности для пропуска байт в процессе получения. В этом случае параметр `dataSize` должно иметь значение, возвращаемое [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md) метод.  
  
## <a name="see-also"></a>См. также  
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)
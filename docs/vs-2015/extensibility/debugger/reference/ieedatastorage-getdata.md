---
title: IEEDataStorage::GetData | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d0d23ecbc348d4aab4fdbbb83abaaba54fdad345
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51751089"
---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Получает указанное число байтов из объекта.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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


---
title: 'Иидатастораже:: GetData | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEDataStorage::GetData
helpviewer_keywords:
- IEEDataStorage::GetData
ms.assetid: 4d384039-73d4-40b4-ace6-a2474c546397
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a58f644a71601b16317c4fe63271f4f816da77d4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149296"
---
# <a name="ieedatastoragegetdata"></a>IEEDataStorage::GetData
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Извлекает указанное число байтов из объекта.  
  
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
 окне Число извлекаемых байтов ( `data` массив должен содержать по крайней мере это число байтов).  
  
 `sizeGotten`  
 заполняет Возвращает число фактически извлеченных байтов.  
  
 `data`  
 [вход, выход] Массив, в который заполняются запрошенные данные.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Этот метод рекомендуется использовать для извлечения всех байтов данных в локальный массив, так как в процессе извлечения невозможно пропускать байты. В этом случае параметр `dataSize` должен быть значением, возвращаемым методом метода [resize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md) .  
  
## <a name="see-also"></a>См. также:  
 [иидатастораже](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [GetSize](../../../extensibility/debugger/reference/ieedatastorage-getsize.md)

---
title: IDiaPropertyStorage::ReadLONG | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadLONG
ms.assetid: 32054cbc-db55-4513-a1b4-de80e77aac8a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: aefa38870d3639b2277dd4af2c38d04b8fbb7c00
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53889982"
---
# <a name="idiapropertystoragereadlong"></a>IDiaPropertyStorage::ReadLONG
Считывает `LONG` значения в наборе свойств.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT ReadDLONG (   
   PROPID id,  
   LONG*  pValue  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `id`  
 [in] Идентификатор свойства для чтения (`PROPID` определяется в файле WTypes.h как `ULONG`).  
  
 `pValue`  
 [out] Возвращает значение свойства.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Возвращает `E_INVALIDARG` Если свойство не имеет типа `LONG`.  
  
## <a name="remarks"></a>Примечания  
 Объект `LONG` определяется Windows как 32-разрядное целое число со знаком.  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
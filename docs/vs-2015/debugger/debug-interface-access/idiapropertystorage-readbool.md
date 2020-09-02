---
title: 'Идиапропертистораже:: Реадбул | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBOOL
ms.assetid: ad1822db-4572-48f7-9919-f8137f6701f2
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 64eee421a5ed5bd46a64b51694d913a4f2dc4d41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538880"
---
# <a name="idiapropertystoragereadbool"></a>IDiaPropertyStorage::ReadBOOL
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Считывает `BOOL` значения в наборе свойств.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT ReadBOOL (   
   PROPID id,  
   BOOL*  pValue  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `id`  
 окне Идентификатор считываемого свойства ( `PROPID` определяется в втипес. h как `ULONG` ).  
  
 `pValue`  
 заполняет Возвращает значение свойства.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки. Возвращает значение, `E_INVALIDARG` Если свойство не относится к типу `BOOL` .  
  
## <a name="remarks"></a>Remarks  
 Для обеспечения единообразия результатов следует интерпретировать `BOOL` значение, чтобы ненулевые значения были `TRUE` и нулевые `FALSE` .  
  
## <a name="see-also"></a>См. также:  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)

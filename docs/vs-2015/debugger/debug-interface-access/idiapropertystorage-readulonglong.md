---
title: 'Идиапропертистораже:: Реадулонглонг | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadULONGLONG
ms.assetid: f80a2e24-5744-4fec-bab0-3ed51aef6e58
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6da509e226a612e80a10ca0759b5e264f31a1e13
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538685"
---
# <a name="idiapropertystoragereadulonglong"></a>IDiaPropertyStorage::ReadULONGLONG
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Считывает `ULONGLONG` значения в наборе свойств.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT ReadULONGLONG (   
   PROPID     id,  
   ULONGLONG* pValue  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `id`  
 окне Идентификатор считываемого свойства ( `PROPID` определяется в втипес. h как `ULONG` ).  
  
 `pValue`  
 заполняет Возвращает значение свойства.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки. Возвращает значение, `E_INVALIDARG` Если свойство не относится к типу `ULONGLONG` .  
  
## <a name="remarks"></a>Remarks  
 `ULONGLONG`Определено Windows как 64-разрядное целое число без знака.  
  
## <a name="see-also"></a>См. также:  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)

---
title: "IDiaPropertyStorage::ReadBSTR | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaPropertyStorage::ReadBSTR
ms.assetid: 7214643b-3286-48ed-90aa-0fe95b4cae5b
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 93ab7271ccef1819e16e4cdb4c690f82bfaeec35
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiapropertystoragereadbstr"></a>IDiaPropertyStorage::ReadBSTR
Считывает `BSTR` значений в наборе свойств.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT ReadBSTR (   
   PROPID id,  
   BSTR*  pValue  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `id`  
 [in] Идентификатор свойства для чтения (`PROPID` определяется в файле WTypes.h как `ULONG`).  
  
 `pValue`  
 [out] Возвращает значение свойства.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки. Возвращает `E_INVALIDARG` Если свойство не имеет типа `BSTR`.  
  
## <a name="remarks"></a>Примечания  
 Объект `BSTR` определяется операционной системой Windows как строку расширенных символов с завершающим нулевым символом.  
  
## <a name="see-also"></a>См. также  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
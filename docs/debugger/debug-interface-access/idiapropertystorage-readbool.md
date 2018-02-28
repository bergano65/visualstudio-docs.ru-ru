---
title: "IDiaPropertyStorage::ReadBOOL | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBOOL
ms.assetid: ad1822db-4572-48f7-9919-f8137f6701f2
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: e7f146222e76ff0f4de9f30140064e7bdd08a358
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idiapropertystoragereadbool"></a>IDiaPropertyStorage::ReadBOOL
Считывает `BOOL` значений в наборе свойств.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT ReadBOOL (   
   PROPID id,  
   BOOL*  pValue  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `id`  
 [in] Идентификатор свойства для чтения (`PROPID` определяется в файле WTypes.h как `ULONG`).  
  
 `pValue`  
 [out] Возвращает значение свойства.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки. Возвращает `E_INVALIDARG` Если свойство не имеет типа `BOOL`.  
  
## <a name="remarks"></a>Примечания  
 Согласованные результаты интерпретации `BOOL` чтобы для ненулевых значений являются `TRUE` и ноль является `FALSE`.  
  
## <a name="see-also"></a>См. также  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
---
title: "IDiaPropertyStorage::ReadULONGLONG | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaPropertyStorage::ReadULONGLONG
ms.assetid: f80a2e24-5744-4fec-bab0-3ed51aef6e58
caps.latest.revision: "9"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 997efbd4528312a18563a6cc606516692f7ca9ee
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiapropertystoragereadulonglong"></a>IDiaPropertyStorage::ReadULONGLONG
Считывает `ULONGLONG` значений в наборе свойств.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT ReadULONGLONG (   
   PROPID     id,  
   ULONGLONG* pValue  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `id`  
 [in] Идентификатор свойства для чтения (`PROPID` определяется в файле WTypes.h как `ULONG`).  
  
 `pValue`  
 [out] Возвращает значение свойства.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки. Возвращает `E_INVALIDARG` Если свойство не имеет типа `ULONGLONG`.  
  
## <a name="remarks"></a>Примечания  
 Объект `ULONGLONG` определяется операционной системой Windows как 64-разрядное целое число без знака.  
  
## <a name="see-also"></a>См. также  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)
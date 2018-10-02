---
title: IDiaPropertyStorage::ReadBOOL | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadBOOL
ms.assetid: ad1822db-4572-48f7-9919-f8137f6701f2
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a518bf3fd92ed8cc353c77cc9c62a98f2fd0d62
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559153"
---
# <a name="idiapropertystoragereadbool"></a>IDiaPropertyStorage::ReadBOOL
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDiaPropertyStorage::ReadBOOL](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/idiapropertystorage-readbool).  
  
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
 [in] Идентификатор свойства для чтения (`PROPID` определяется в файле WTypes.h как `ULONG`).  
  
 `pValue`  
 [out] Возвращает значение свойства.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки. Возвращает `E_INVALIDARG` Если свойство не имеет типа `BOOL`.  
  
## <a name="remarks"></a>Примечания  
 Согласованные результаты интерпретировать `BOOL` значение таким образом, ненулевыми значениями `TRUE` а нулевое — `FALSE`.  
  
## <a name="see-also"></a>См. также  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)




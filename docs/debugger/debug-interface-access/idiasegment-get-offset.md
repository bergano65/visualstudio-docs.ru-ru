---
title: "IDiaSegment::get_offset | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSegment::get_offset method
ms.assetid: 97415ac6-b072-4e3c-9dd3-73087ae605fc
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4e0b3c12cb32bd2582cdfc603dbdde5623c6f77e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiasegmentgetoffset"></a>IDiaSegment::get_offset
Возвращает смещение в сегменты, где начинается раздел.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_offset (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает смещение сегментов, в которой начинается раздел.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если это свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
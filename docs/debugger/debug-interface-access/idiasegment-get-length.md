---
title: "IDiaSegment::get_length | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSegment::get_length method
ms.assetid: 5d92e394-649b-49f2-bce7-12dd9d666d85
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a9adb4bc476186b7b78d6cc8bba9f3d5d2b7639e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiasegmentgetlength"></a>IDiaSegment::get_length
Возвращает число байтов в сегменте.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_ length (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает число байтов в сегменте.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если это свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
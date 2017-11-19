---
title: "IDiaSegment::get_addressSection | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSegment::get_addressSection method
ms.assetid: 360b61b1-69b1-4a8b-ba37-97a1d835ac53
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b912736465a5a518d3a0c3f2412617f8edca3ac3
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiasegmentgetaddresssection"></a>IDiaSegment::get_addressSection
Извлекает номер раздела, который сопоставляется этого сегмента.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_addressSection (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает номер раздела, который сопоставляется этого сегмента.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если это свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)
---
title: "IDiaEnumFrameData::frameByRVA | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumFrameData::frameByRVA method
ms.assetid: 4b8dec05-e76c-4cc4-9644-2369d583849f
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b6af518b68c8e9384ff701305bce9253eedac56
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumframedataframebyrva"></a>IDiaEnumFrameData::frameByRVA
Возвращает кадр, относительный виртуальный адрес (RVA).  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT frameByRVA(   
   DWORD           relativeVirtualAddress,  
   IDiaFrameData** frame  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 relativeVirtualAddress  
 [in] Относительный виртуальный адрес фрейма, представляющие интерес.  
  
 фрейм  
 [out] Возвращает [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) объект, представляющий фрейма, содержащего указанный адрес.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если данные не кадра, соответствующей указанному адресу. В противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
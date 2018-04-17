---
title: IDiaEnumFrameData::frameByRVA | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::frameByRVA method
ms.assetid: 4b8dec05-e76c-4cc4-9644-2369d583849f
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: df14e29d1bd1af5589a91c42e309d8a7f6fc316a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
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
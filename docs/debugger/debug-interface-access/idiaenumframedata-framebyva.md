---
title: IDiaEnumFrameData::frameByVA | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumFrameData::frameByVA method
ms.assetid: 0b1e441b-710a-46d8-8060-bed39071c834
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: da06e04515b2f0aac88e3efb0a1271b917e15638
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idiaenumframedataframebyva"></a>IDiaEnumFrameData::frameByVA
Возвращает кадр, виртуальный адрес (VA).  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT frameByVA(   
   ULONGLONG       virtualAddress,  
   IDiaFrameData** frame  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 virtualAddress  
 [in] VA кадра интерес.  
  
 фрейм  
 [out] Возвращает [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) , представляющий фрейма, содержащего указанный адрес.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если данные не кадра, соответствующей указанному адресу. В противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
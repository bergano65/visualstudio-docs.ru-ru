---
title: IDiaFrameData::get_lengthBlock | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_lengthBlock method
ms.assetid: 2e54deb7-7744-428e-913c-1d47a2aa89b0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b1fc4d1bea8a1e7829deb6ea1500137fd136f0a6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idiaframedatagetlengthblock"></a>IDiaFrameData::get_lengthBlock
Получает длину в байтах блока кода, описываемого фрейма.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_lengthBlock (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает число байтов кода в кадре.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если это свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Значение, возвращаемое этим методом, обычно используется в интерпретации строки программы (в разделе [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) метод для определения строки программы).  
  
## <a name="see-also"></a>См. также  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)
---
title: IDiaFrameData::get_allocatesBasePointer | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaFrameData::get_allocatesBasePointer method
ms.assetid: 8a33db5d-008c-4fe5-b64f-210c9b77f686
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fdeab20ee39dc62688f7cf4604e00117d9eb676f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idiaframedatagetallocatesbasepointer"></a>IDiaFrameData::get_allocatesBasePointer
Возвращает флаг, указывающий, выделен ли указатель базы кода в этом диапазоне. Этот метод является устаревшим.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_allocatesBasePointer (   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает `TRUE` Если базового указателя выделяется; в противном случае возвращает `FALSE`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если это свойство не поддерживается. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Это свойство следует использовать только в коде, которые ранее доступны FPO_DATA или при возвращенной строке программы [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) метод `NULL`. В противном случае программа строка содержит все сведения, необходимые для вычисления предыдущие значения регистра.  
  
## <a name="see-also"></a>См. также  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)
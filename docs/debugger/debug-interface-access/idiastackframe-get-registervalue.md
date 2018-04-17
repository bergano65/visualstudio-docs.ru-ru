---
title: IDiaStackFrame::get_registerValue | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackFrame::get_registerValue method
ms.assetid: cbe3d8ac-319a-40ac-bc3e-4eb81b2d7807
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e38d94d5c79438b103b4db9a16164ffe482c356b
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idiastackframegetregistervalue"></a>IDiaStackFrame::get_registerValue
Получает значение указанного регистра, как хранящиеся в кадре стека.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_registerValue(  
   ULONG      registerIndex,  
   ULONGLONG *pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `registerIndex`  
 [in] Один из [CV_HREG_e-перечисление](../../debugger/debug-interface-access/cv-hreg-e.md) значений перечисления.  
  
 `pRetVal`  
 [out] Значение, хранящееся в регистре.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)   
 [Перечисление CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md)
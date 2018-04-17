---
title: IDiaStackWalkFrame::put_registerValue | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::put_registerValue method
ms.assetid: 2d8b79b6-7240-43fe-b24e-e4ff3e2c15b0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3e9c2d0919d9834ae6d1da5e1f3a7eabd238f6cb
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idiastackwalkframeputregistervalue"></a>IDiaStackWalkFrame::put_registerValue
Задает значение регистра.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT put_registerValue (   
   DWORD     index,  
   ULONGLONG NewVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `index`  
 [in] Значение из [CV_HREG_e-перечисление](../../debugger/debug-interface-access/cv-hreg-e.md) перечисление, определяющее регистра для записи.  
  
 `NewVal`  
 [in] Новое значение регистра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)   
 [Перечисление CV_HREG_e](../../debugger/debug-interface-access/cv-hreg-e.md)
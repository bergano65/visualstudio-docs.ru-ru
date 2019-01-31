---
title: IDiaStackWalkFrame::searchForReturnAddress | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::searchForReturnAddress method
ms.assetid: 1a54c50d-94af-4a43-ac4e-d80c5df156c3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f552e9e21baf0be0b8ad2f1a0138323ea09c0502
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55009236"
---
# <a name="idiastackwalkframesearchforreturnaddress"></a>IDiaStackWalkFrame::searchForReturnAddress
Выполняет поиск указанного кадра стека для ближайшего обратный адрес функции.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT searchForReturnAddress (   
   IDiaFrameData* frame,  
   ULONGLONG*     returnAddress  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `frame`  
 [in] [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) , представляющий текущий кадр стека.  
  
 `returnAddress`  
 [out] Возвращает обратный адрес ближайшего функции.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
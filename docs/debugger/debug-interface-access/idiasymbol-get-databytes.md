---
title: IDiaSymbol::get_dataBytes | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_dataBytes method
ms.assetid: 5eb37179-20d8-44ae-a72a-405c1b0435c4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d70ede5bdade583d0b25787f7c97c345cef9cbe1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54925361"
---
# <a name="idiasymbolgetdatabytes"></a>IDiaSymbol::get_dataBytes
Извлекает байты данных символов OEM.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_dataBytes (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `cbData`  
 [in] Размер буфера для хранения данных.  
  
 `pcbData`  
 [out] Возвращает число байтов, записанных, или, если `data` параметр `NULL`, возвращает число доступных байтов.  
  
 `data[]`  
 [out] Буфер, который заполняется байт данных.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.  
  
## <a name="requirements"></a>Требования  
  
|Требование|Описание|  
|-----------------|-----------------|  
|Заголовок:|dia2.h|  
|Версия:|ПАКЕТ SDK для версии 7.0|  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
---
title: IDiaSymbol::get_offset | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_offset method
ms.assetid: 8292bb08-4dc8-4663-beb4-258f5d5a448d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a336f580d110878d41dda036d626e1033a8c137
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736953"
---
# <a name="idiasymbolgetoffset"></a>IDiaSymbol::get_offset
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Получает смещение расположения символов. Используется, когда [перечисление LocationType](../../debugger/debug-interface-access/locationtype.md) — `LocIsRegRel` или `LocIsBitField`.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT get_offset (   
   LONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает смещение в байтах расположения символов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.  
  
## <a name="remarks"></a>Примечания  
 Смещение считается от какой-то момент известных обнаружены. Например, смещение `LocIsBitField` расположение типом обычно является от начала содержащего класса.  
  
## <a name="requirements"></a>Требования  
  
|Требование|Описание:|  
|-----------------|-----------------|  
|Заголовок:|dia2.h|  
|Версия:|ПАКЕТ SDK для версии 7.0|  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление LocationType](../../debugger/debug-interface-access/locationtype.md)




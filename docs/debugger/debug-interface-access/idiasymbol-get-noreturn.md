---
title: "IDiaSymbol::get_noReturn | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_noReturn method
ms.assetid: 704c1cc0-5b84-4334-a02a-70f43aff39d5
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f25fdf93cbe70f3a867e7c8c581e9d7601cc136
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetnoreturn"></a>IDiaSymbol::get_noReturn
Возвращает флаг, указывающий, является ли функция был помечен как никогда не возвращает [noreturn](/cpp/cpp/noreturn) атрибута.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_noReturn(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 pFlag  
 [out] Возвращает `TRUE` Если функция была объявлена как никогда не возвращает `noreturn` атрибут; в противном случае возвращает `FALSE`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает свойство недоступно для символа.  
  
## <a name="requirements"></a>Требования  
  
|Требование|Описание|  
|-----------------|-----------------|  
|Заголовок:|dia2.h|  
|Версия:|ПАКЕТ SDK для версии 8.0|  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [noreturn](/cpp/cpp/noreturn)
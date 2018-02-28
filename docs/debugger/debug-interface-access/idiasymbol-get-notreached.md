---
title: "IDiaSymbol::get_notReached | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_notReached method
ms.assetid: e44ba922-6cda-40c2-9b62-44e5a8628e63
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 8989a4ac2ed8c7688f0ffc37a71901d44e16c343
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgetnotreached"></a>IDiaSymbol::get_notReached
Возвращает флаг, указывающий, является ли функция или метки, никогда не будет достигнут.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_notReached(  
   BOOL *pFlag  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 pFlag  
 [out] Возвращает `TRUE` Если функция или метки, никогда не будет достигнут; в противном случае возвращает `FALSE`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает свойство недоступно для символа.  
  
## <a name="requirements"></a>Требования  
  
|Требование|Описание:|  
|-----------------|-----------------|  
|Заголовок:|dia2.h|  
|Версия:|ПАКЕТ SDK для версии 8.0|  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
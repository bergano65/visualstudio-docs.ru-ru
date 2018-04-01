---
title: IDiaSymbol::get_framePointerPresent | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_framePointerPresent method
ms.assetid: d036090a-1651-454d-9130-b798f58ba053
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: f6deaaabfcc4befca3079f4ef177c35f6b684e99
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idiasymbolgetframepointerpresent"></a>IDiaSymbol::get_framePointerPresent
Возвращает флаг, указывающий, присутствует ли указатель фрейма. Используется, когда [перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) равно `SymTagFunction`.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_framePointerPresent(   
   BOOL* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out]] Возвращает `TRUE` если указатель фрейма существует; в противном случае возвращает `FALSE`.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает свойство недоступно для символа.  
  
## <a name="remarks"></a>Примечания  
  
## <a name="requirements"></a>Требования  
 Заголовок: Dia2.h  
  
 Библиотека: diaguids.lib  
  
 Библиотека DLL: msdia100.dll  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
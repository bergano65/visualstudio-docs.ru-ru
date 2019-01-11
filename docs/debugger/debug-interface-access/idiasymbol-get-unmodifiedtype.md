---
title: IDiaSymbol::get_unmodifiedType | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_unmodifiedType method
ms.assetid: bf914dc0-ff84-4f5d-9f75-1733b17f3be0
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fe76a3155941c9f7a3c6cc02d02291e61c8e4e89
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53898561"
---
# <a name="idiasymbolgetunmodifiedtype"></a>IDiaSymbol::get_unmodifiedType
Извлекает исходный тип для этого символа. Используется, когда [перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) присваивается тип.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_unmodifiedType(   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) , представляющий исходный тип, от этого символа.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает, что свойство недоступно для символа.  
  
## <a name="remarks"></a>Примечания  
 Текущий тип является модификацией возвращаемого исходного типа. Исходный тип символа определяется сначала начало тип символа и затем опроса, возвращаемый тип для исходного типа. Обратите внимание, что некоторые символы не могут иметь измененный тип исходного типа.  
  
## <a name="requirements"></a>Требования  
 Заголовок: dia2.h  
  
 Библиотека: diaguids.lib  
  
 Библиотеки DLL: msdia100.dll  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
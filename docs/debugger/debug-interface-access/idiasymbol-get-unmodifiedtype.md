---
title: "IDiaSymbol::get_unmodifiedType | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_unmodifiedType method
ms.assetid: bf914dc0-ff84-4f5d-9f75-1733b17f3be0
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a24b85ac16f9837a4e28674567341f00a993bf9f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetunmodifiedtype"></a>IDiaSymbol::get_unmodifiedType
Получает исходный тип для этого символа. Используется, когда [SymTagEnum-перечисление](../../debugger/debug-interface-access/symtagenum.md) установите тип.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_unmodifiedType(   
   IDiaSymbol** pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) объект, представляющий исходный тип для этого символа.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает `S_FALSE` или код ошибки.  
  
> [!NOTE]
>  Возвращаемое значение `S_FALSE` означает свойство недоступно для символа.  
  
## <a name="remarks"></a>Примечания  
 Текущий тип — это изменение возвращенных исходного типа. Сначала получить тип символа, и затем опроса, возвращенный тип исходный тип можно определить исходный тип для символа. Обратите внимание, что некоторые символы не могут иметь измененный тип исходного типа.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Dia2.h  
  
 Библиотека: diaguids.lib  
  
 Библиотека DLL: msdia100.dll  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)
---
title: "IDiaSymbol::get_paramBasePointerRegisterId | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaSymbol::get_paramBasePointerRegisterId method
ms.assetid: 9f5caeb4-5c88-4054-bf8b-50d34bbbf8c5
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e542c6ea2e242149f601f2d74d4c17d3bede5b2b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiasymbolgetparambasepointerregisterid"></a>IDiaSymbol::get_paramBasePointerRegisterId
Извлекает идентификатор регистра, который содержит базовый указатель на параметры. Используется, когда [перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md) равно `SymTagFunction`.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT get_paramBasePointerRegisterId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pRetVal`  
 [out] Возвращает идентификатор регистра, который содержит базовый указатель на параметры.  
  
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
---
title: IDiaSymbol::findChildrenExByAddr | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenExByAddr
ms.assetid: c1e7885d-2d15-4529-9ac2-32dd22efe31c
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7398f3afdf8a6895d0feaec35ca33b95e9054060
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49834868"
---
# <a name="idiasymbolfindchildrenexbyaddr"></a>IDiaSymbol::findChildrenExByAddr
Получает дочерние узлы символа, которые являются допустимыми с указанного адреса.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT findChildrenExByAddr (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   DWORD             address,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `symtag`  
 [in] Задает теги символов требуется получить дочерние элементы, как определено в [перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md). Значение `SymTagNull` для всех дочерних элементов, требуется получить.  
  
 `name`  
 [in] Задает имя используемого дочерние элементы должны быть получены. Значение `NULL` для всех дочерних элементов, требуется получить.  
  
 `compareFlags`  
 [in] Задает параметры сравнения для применения к совпадению имен. Значения из [перечисление NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md) перечисления можно использовать отдельно или в сочетании.  
  
 `address`  
 [in] Адрес символа.  
  
 `ppResult`  
 [out] Возвращает [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) извлечь объект, содержащий список дочерних символов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает `S_OK` Если по крайней мере одного дочернего элемента этот символ найден, или возвращает `S_FALSE` дочерние элементы не найдены; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Локальные символы, которые возвращаются включают сведения о динамической диапазона.  
  
## <a name="requirements"></a>Требования  
 Заголовок: Dia2.h  
  
 Библиотека: diaguids.lib  
  
 Библиотеки DLL: msdia100.dll  
  
## <a name="see-also"></a>См. также  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [Перечисление NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)
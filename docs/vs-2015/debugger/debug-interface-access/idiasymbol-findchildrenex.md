---
title: 'IDiaSymbol:: Финдчилдренекс | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildrenEx
ms.assetid: 6e045045-da8c-4338-9423-81a1ca20c405
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0ee0ee9938ba2529afd7ea437c56761e1768e8cd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150014"
---
# <a name="idiasymbolfindchildrenex"></a>IDiaSymbol::findChildrenEx
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Возвращает дочерние элементы символа. Возвращаемые локальные символы включают сведения о диапазоне в реальном времени, если программа компилируется с оптимизацией.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT findChildrenEx (   
   enum SymTagEnum   symtag,  
   LPCOLESTR         name,  
   DWORD             compareFlags,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `symtag`  
 окне Задает Теги символов для извлекаемых дочерних элементов, как определено в [перечислении симтаженум](../../debugger/debug-interface-access/symtagenum.md). Задайте значение, чтобы `SymTagNull` получить все дочерние элементы.  
  
 `name`  
 окне Указывает имя извлекаемых дочерних элементов. Задайте значение, чтобы `NULL` получить все дочерние элементы.  
  
 `compareFlags`  
 окне Задает параметры сравнения, применяемые к соответствию имен. Значения из перечисления [перечисления намесеарчоптионс](../../debugger/debug-interface-access/namesearchoptions.md) можно использовать отдельно или в сочетании.  
  
 `ppResult`  
 заполняет Возвращает объект [идиаенумсимболс](../../debugger/debug-interface-access/idiaenumsymbols.md) , содержащий список извлеченных дочерних символов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK` , если найден хотя бы один дочерний элемент символа, или значение `S_FALSE` , если не найдено потомков. в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Этот метод является расширенной версией [IDiaSymbol:: финдчилдрен](../../debugger/debug-interface-access/idiasymbol-findchildren.md).  
  
## <a name="requirements"></a>Требования  
 Заголовок: Dia2. h  
  
 Библиотека: диагуидс. lib  
  
 DLL: msdia100.dll  
  
## <a name="see-also"></a>См. также:  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление Симтаженум](../../debugger/debug-interface-access/symtagenum.md)   
 [идиаенумсимболс](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession:: Финдчилдрен](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [Перечисление NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)

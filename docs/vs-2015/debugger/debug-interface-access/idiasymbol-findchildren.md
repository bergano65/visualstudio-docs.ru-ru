---
title: 'IDiaSymbol:: Финдчилдрен | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::findChildren method
ms.assetid: 5fe7573a-e48b-428d-9c17-7421b7209246
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a09a62a2e6b94dbccda3afce4bdd286270149c15
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150032"
---
# <a name="idiasymbolfindchildren"></a>IDiaSymbol::findChildren
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Возвращает дочерние элементы символа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT findChildren (   
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
 Возвращает значение `S_OK` , если найден хотя бы один дочерний элемент символа, или возвращает значение, `S_FALSE` Если дочерних элементов не найдено; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Этот метод идентичен вызову метода [IDiaSession:: финдчилдрен](../../debugger/debug-interface-access/idiasession-findchildren.md) с этим символом в качестве первого параметра.  
  
## <a name="see-also"></a>См. также:  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление Симтаженум](../../debugger/debug-interface-access/symtagenum.md)   
 [идиаенумсимболс](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession:: Финдчилдрен](../../debugger/debug-interface-access/idiasession-findchildren.md)   
 [Перечисление NameSearchOptions](../../debugger/debug-interface-access/namesearchoptions.md)

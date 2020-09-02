---
title: 'IDiaSymbol:: Финдинлинилинесбирва | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: ac108db1-9dbf-4dc4-bf48-159ca8d3725c
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1de9a2803ae82eccbcb96bda5b49df0cfb94444d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149930"
---
# <a name="idiasymbolfindinlineelinesbyrva"></a>IDiaSymbol::findInlineeLinesByRVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Извлекает перечисление, позволяющее клиенту выполнять итерацию по сведениям о номере строки всех функций, встроенных, прямо или косвенно, в этом символе в пределах указанного относительного виртуального адреса (RVA).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT findInlineeLinesByRVA (    DWORD                 rva,   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `rva`  
 окне Указывает адрес в виде RVA.  
  
 `length`  
 окне Указывает диапазон адресов (в байтах), который охватывает этот запрос.  
  
 `ppResult`  
 заполняет Содержит `IDiaEnumLineNumbers` объект, содержащий список извлекаемых номеров строк.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление Симтаженум](../../debugger/debug-interface-access/symtagenum.md)   
 [идиаенумлиненумберс](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)

---
title: IDiaSymbol::findInlineeLinesByVA | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: 61427d33-30d2-4ac9-9bd6-c58c6c705072
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7f1bb0af59cfa4c9ee3ba27003f985361cde9241
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58980638"
---
# <a name="idiasymbolfindinlineelinesbyva"></a>IDiaSymbol::findInlineeLinesByVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Возвращает перечисление, которое позволяет клиенту для выполнения итерации по информация о номере строки всех функций, которые являются встроенными, напрямую или косвенно, в этот символ в указанный виртуальный адрес (VA).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT findInlineeLinesByVA (   
   ULONGLONG             va,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `va`  
 [in] Указывает адрес как ва.  
  
 `length`  
 [in] Указывает диапазон адресов, в байтах, чтобы охватить с этим запросом.  
  
 `ppResult`  
 [out] Содержит `IDiaEnumLineNumbers` , содержащий список номеров строк, возвращаемых.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Перечисление SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)

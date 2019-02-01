---
title: IDiaEnumLineNumbers::Item | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumLineNumbers::Item method
ms.assetid: 08efbeaf-22f7-49e9-96a8-bb906dfe4fd8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a4733756a8de69348623049d3ae4997847eb32bb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54925571"
---
# <a name="idiaenumlinenumbersitem"></a>IDiaEnumLineNumbers::Item
Получает номер строки с помощью индекса.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT Item (   
   DWORD            index,  
   IDiaLineNumber** lineNumber  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 индекс  
 [in] Индекс [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) извлекаемый объект. Индекс находится в диапазоне от 0 до `count`-1, где `count` возвращается [IDiaEnumLineNumbers::get_Count](../../debugger/debug-interface-access/idiaenumlinenumbers-get-count.md) метод.  
  
 lineNumber  
 [out] Возвращает [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md) объект, представляющий номер требуемой строки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)   
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)
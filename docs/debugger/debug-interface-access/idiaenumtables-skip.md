---
title: IDiaEnumTables::Skip | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Skip method
ms.assetid: 5c9db956-0654-4f1a-8775-530aa980d8ec
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4791553e15754ec24ad949dcd0abb9fb30190ce7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53989433"
---
# <a name="idiaenumtablesskip"></a>IDiaEnumTables::Skip
Пропускает указанное число таблиц в последовательности перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `celt`  
 [in] Количество таблиц в последовательности перечисления для пропуска.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает `S_FALSE` Если отсутствуют дополнительные таблицы, чтобы пропустить.  
  
## <a name="see-also"></a>См. также раздел  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)
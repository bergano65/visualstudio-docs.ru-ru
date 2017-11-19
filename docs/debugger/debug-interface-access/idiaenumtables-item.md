---
title: "IDiaEnumTables::Item | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: IDiaEnumTables::Item method
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
caps.latest.revision: "11"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 26acf7b8f9ad54a1ef1ed25497cd408c51c745c5
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="idiaenumtablesitem"></a>IDiaEnumTables::Item
Возвращает таблицу с помощью индекса или имени.  
  
## <a name="syntax"></a>Синтаксис  
  
```C++  
HRESULT Item (   
   VARIANT     index,  
   IDiaTable** table  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `index`  
 [in] Индекс или имя [IDiaTable](../../debugger/debug-interface-access/idiatable.md) требуется получить. Если используется вариант целое число, его должны находиться в диапазоне от 0 до `count`-1, где `count` как возвращаемый [IDiaEnumTables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md) метод.  
  
 `table`  
 [out] Возвращает [IDiaTable](../../debugger/debug-interface-access/idiatable.md) объект, представляющий нужную таблицу.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Если указан вариант строка, строка имен конкретной таблицы. Имя должно быть одно из имен таблиц, определенных в [константы (SDK отладки интерфейса доступа)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md).  
  
## <a name="example"></a>Пример  
  
```C++  
VARIANT var;  
var.vt = VT_BSTR;  
var.bstrVal = SysAllocString(DiaTable_Symbols );  
IDiaTable* pTable;  
pEnumTables->Item( var, &pTable );  
```  
  
## <a name="see-also"></a>См. также  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaEnumTables::get_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)   
 [Константы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)
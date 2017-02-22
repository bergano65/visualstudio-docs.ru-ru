---
title: "IDiaEnumTables::Item | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaEnumTables::Item - метод"
ms.assetid: d65ab262-10c6-48ce-95a3-b5e4cb2c85af
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaEnumTables::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает таблицу с помощью индекса или имени.  
  
## Синтаксис  
  
```cpp#  
HRESULT Item (   
   VARIANT     index,  
   IDiaTable** table  
);  
```  
  
#### Параметры  
 `index`  
 \[in\] индекс или имя [IDiaTable](../../debugger/debug-interface-access/idiatable.md) требуется извлечь.  Если вариант integer используется, то он должен быть в диапазоне от 0 до `count`\-1, где  `count` возвращается как  [IDiaEnumTables::get\_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md) метод.  
  
 `table`  
 \[out\] возвращает [IDiaTable](../../debugger/debug-interface-access/idiatable.md) объект, представляющий нужную таблицу.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Если версии строки задан, то имена строки указанная таблица.  Имя должно быть одним из имен таблиц, как определено в [Константы \(SDK для доступа к интерфейсу отладки\)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md).  
  
## Пример  
  
```cpp#  
VARIANT var;  
var.vt = VT_BSTR;  
var.bstrVal = SysAllocString(DiaTable_Symbols );  
IDiaTable* pTable;  
pEnumTables->Item( var, &pTable );  
```  
  
## См. также  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)   
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)   
 [IDiaEnumTables::get\_Count](../../debugger/debug-interface-access/idiaenumtables-get-count.md)   
 [Константы \(SDK для доступа к интерфейсу отладки\)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)
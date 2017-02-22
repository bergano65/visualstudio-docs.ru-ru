---
title: "Константы (SDK для доступа к интерфейсу отладки) | Microsoft Docs"
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
  - "константы, пакет SDK для доступа к интерфейсу отладки"
  - "пакет SDK для доступа к интерфейсу отладки, константы"
ms.assetid: aca4ec77-bc08-4cdd-a6ce-8d4a28ea5ea3
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Константы (SDK для доступа к интерфейсу отладки)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Эти константы строки можно использовать для определения различных разделов отладочный файл базы данных программы \(PDB\) по пакету SDK для доступа к интерфейсу отладки.  
  
## Константы  
 Следующие объявлены как макросов C\/C\+\+.  
  
|Макрос|Значение|  
|------------|--------------|  
|`DiaTable_Symbols`|Символы" l "|  
|`DiaTable_Sections`|L " инструкции"|  
|`DiaTable_SrcFiles`|l " SourceFiles"|  
|`DiaTable_LineNums`|LineNumbers" l "|  
|`DiaTable_SegMap`|l " SegmentMap"|  
|`DiaTable_Dbg`|Dbg\-файлы" l "|  
|`DiaTable_InjSrc`|l " InjectedSource"|  
|`DiaTable_FrameData`|l " FrameData"|  
  
## Пример  
 Ниже приведен пример с помощью одного из следующих символов:  
  
```cpp#  
HRESULT GetSymbolTable(IDiaEnumTables *pEnumTables, IDiaTable **pTable)  
{  
    HRESULT hr;  
    VARIANT var;  
    var.vt      = VT_BSTR;  
    var.bstrVal = SysAllocString( DiaTable_Symbols );  
    hr = pEnumTables->Item( var, pTable );  
    return(hr);  
}  
```  
  
## Требования  
 Заголовок: dia2.h  
  
## См. также  
 [Справочник](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)   
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Интерфейсы \(SDK для доступа к интерфейсу отладки\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)
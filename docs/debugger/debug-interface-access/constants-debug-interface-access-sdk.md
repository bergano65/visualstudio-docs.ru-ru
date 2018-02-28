---
title: "Константы (SDK для доступа к интерфейсу отладки) | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- constants, DIA SDK
- DIA SDK, constants
ms.assetid: aca4ec77-bc08-4cdd-a6ce-8d4a28ea5ea3
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 8241190650bf395e1e4e2467b4862119cd2b10dc
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="constants-debug-interface-access-sdk"></a>Константы (SDK для доступа к интерфейсу отладки)
Эти строковые константы можно использовать для определения различных разделов отладки (PDB) файл программы через пакет SDK для доступа к интерфейсу отладки.  
  
## <a name="constants"></a>Константы  
 Следующие объявляются как макросов C/C++.  
  
|Макрос|Значение|  
|-----------|-----------|  
|`DiaTable_Symbols`|L «Символы»|  
|`DiaTable_Sections`|L «Разделами»|  
|`DiaTable_SrcFiles`|L «SourceFiles»|  
|`DiaTable_LineNums`|L «LineNumbers»|  
|`DiaTable_SegMap`|L «SegmentMap»|  
|`DiaTable_Dbg`|L «Dbg»|  
|`DiaTable_InjSrc`|L «InjectedSource»|  
|`DiaTable_FrameData`|L «FrameData»|  
  
## <a name="example"></a>Пример  
 Ниже приведен пример с использованием одного из следующих символов:  
  
```C++  
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
  
## <a name="requirements"></a>Требования  
 Заголовок: dia2.h  
  
## <a name="see-also"></a>См. также  
 [Ссылка](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)   
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)
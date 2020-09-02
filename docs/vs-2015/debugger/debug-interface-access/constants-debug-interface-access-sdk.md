---
title: Константы (SDK для доступа к интерфейсу отладки) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- constants, DIA SDK
- DIA SDK, constants
ms.assetid: aca4ec77-bc08-4cdd-a6ce-8d4a28ea5ea3
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 931e1ab46793a5ff7e0434949330eaf4dbc820e8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164425"
---
# <a name="constants-debug-interface-access-sdk"></a>Константы (SDK для доступа к интерфейсу отладки)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Эти строковые константы можно использовать для обнаружения различных разделов файла базы данных отладки (PDB) с помощью пакета SDK DIA.  
  
## <a name="constants"></a>Константы  
 Следующие объявления объявляются в виде макросов C/C++.  
  
|Макрос|Значение|  
|-----------|-----------|  
|`DiaTable_Symbols`|L "символы"|  
|`DiaTable_Sections`|L "разделы"|  
|`DiaTable_SrcFiles`|L "SourceFiles"|  
|`DiaTable_LineNums`|L "Линенумберс"|  
|`DiaTable_SegMap`|L "Сегментмап"|  
|`DiaTable_Dbg`|L "DBG"|  
|`DiaTable_InjSrc`|L "Инжектедсаурце"|  
|`DiaTable_FrameData`|L "Фрамедата"|  
  
## <a name="example"></a>Пример  
 Ниже приведен пример использования одного из следующих символов:  
  
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
  
## <a name="requirements"></a>Требования  
 Заголовок: dia2. h  
  
## <a name="see-also"></a>См. также:  
 [IsReference](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)   
 [Перечисления и структуры](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [Интерфейсы (SDK для доступа к интерфейсу отладки)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumTables::Item](../../debugger/debug-interface-access/idiaenumtables-item.md)

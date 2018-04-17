---
title: MODULE_SYMBOL_SEARCH_INFO | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords:
- MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: bb62fb0a830c8c3bf6bb9b7ca186e001573b7b37
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="modulesymbolsearchinfo"></a>MODULE_SYMBOL_SEARCH_INFO
Содержит сведения о пути поиска символов, которые был выполнен поиск состоянии.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
typedef struct _tagSYMBOL_SEARCH_INFO  
{  
   SYMBOL_SEARCH_INFO_FIELDS dwValidFields;  
   BSTR                      bstrVerboseSearchInfo;  
} MODULE_SYMBOL_SEARCH_INFO;  
```  
  
```csharp  
public struct MODULE_SYMBOL_SEARCH_INFO {  
   public uint   dwValidFields;  
   public string bstrVerboseSearchInfo;  
}  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwValidFields`  
 Сочетание флагов из [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) перечисление, указывающее тип поиска сведения, описанные в этой структуре.  
  
 `bstrVerboseSearchInfo`  
 Пути поиска и результаты объединяются в одну строку.  
  
## <a name="remarks"></a>Примечания  
 Эта структура возвращается из вызова [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) метод.  
  
 Если `bstrVerboseSearchInfo` поле не пусто, то он содержит список пути поиска и результаты поиска. Список имеет формат с путем, а затем кнопку с многоточием («...»), а затем результат. Если имеется несколько пар результирующий путь, каждая пара отделяется пару «\r\n» (каретки возврата и перевода строки). Шаблон выглядит следующим образом:  
  
 \<путь >... \<результат > \r\n\<путь >... \<результат > \r\n\<путь >... \<результат >  
  
 Обратите внимание, что последний элемент последовательности \r\n.  
  
 Вот возможного `bstrVerboseSearchInfo` строки, которое было отправлено на стандартный выход.  
  
 `c:\symbols\user32.pdb... File not found.`  
  
 `c:\winnt\symbols\user32.pdb... Version does not match.`  
  
 `\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структур и объединений](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)
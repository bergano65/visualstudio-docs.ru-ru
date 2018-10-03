---
title: MODULE_SYMBOL_SEARCH_INFO | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords:
- MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 074e837a1c0449420d7042539fb4c8dfa0396fe6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568948"
---
# <a name="modulesymbolsearchinfo"></a>MODULE_SYMBOL_SEARCH_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [MODULE_SYMBOL_SEARCH_INFO](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/module-symbol-search-info).  
  
Содержит сведения о пути поиска символов, которые после состоянии.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 Сочетание флагов из [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) перечисления, указывающее, какой тип поиска сведения, описанные в этой структуре.  
  
 `bstrVerboseSearchInfo`  
 Пути поиска и результаты объединяются в одну строку.  
  
## <a name="remarks"></a>Примечания  
 Эта структура возвращается из вызова [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) метод.  
  
 Если `bstrVerboseSearchInfo` поле не пусто, то он содержит список пути поиска и результаты поиска. Путь, а затем кнопку с многоточием («...»), а затем результат имеет формат списка. Если имеется несколько пар результирующий путь, каждая пара отделяется пару «\r\n» (каретки возврата и перевода строки). Шаблон выглядит следующим образом:  
  
 \<путь >... \<результат > \r\n\<путь >... \<результат > \r\n\<путь >... \<результата >  
  
 Обратите внимание, что последний элемент последовательности \r\n.  
  
 Вот возможного `bstrVerboseSearchInfo` строки, который был отправлен на стандартный выход.  
  
 `c:\symbols\user32.pdb... File not found.`  
  
 `c:\winnt\symbols\user32.pdb... Version does not match.`  
  
 `\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)


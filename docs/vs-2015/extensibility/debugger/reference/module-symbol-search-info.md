---
title: MODULE_SYMBOL_SEARCH_INFO | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords:
- MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e2cfbaf8c3756bf758956d1f1e5964d8e9f8f0c8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68205187"
---
# <a name="module_symbol_search_info"></a>MODULE_SYMBOL_SEARCH_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Содержит сведения о состоянии для путей поиска символов, которые были просмотрены.  
  
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
 Сочетание флагов из перечисления [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) , определяющее тип сведений для поиска, описанных в этой структуре.  
  
 `bstrVerboseSearchInfo`  
 Путь поиска и результаты, Объединенные в одну строку.  
  
## <a name="remarks"></a>Remarks  
 Эта структура возвращается из вызова метода [жетсимболинфо](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) .  
  
 Если `bstrVerboseSearchInfo` поле не пусто, то оно содержит список путей поиска и результаты этого поискового запроса. Список форматируется с помощью пути, за которым следует многоточие ("..."), за которым следует результат. Если существует несколько пар результатов пути, каждая пара отделяется парой "\r\n" (возврат каретки или перевод строки). Шаблон выглядит следующим образом:  
  
 \<path>...\<result> \r\n \<path> ... \<result> \r\n \<path> ...\<result>  
  
 Обратите внимание, что последняя запись не содержит последовательность \r\n.  
  
 Ниже приведена возможная `bstrVerboseSearchInfo` строка, отправленная в стандартный выход.  
  
 `c:\symbols\user32.pdb... File not found.`  
  
 `c:\winnt\symbols\user32.pdb... Version does not match.`  
  
 `\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`  
  
## <a name="requirements"></a>Требования  
 Заголовок: мсдбг. h  
  
 Пространство имен: Microsoft. VisualStudio. Debugger. Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также:  
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)

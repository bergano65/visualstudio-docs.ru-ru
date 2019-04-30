---
title: MODULE_SYMBOL_SEARCH_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords:
- MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6886373e521c411c3823b9f15138c8f798a373f4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62913821"
---
# <a name="modulesymbolsearchinfo"></a>MODULE_SYMBOL_SEARCH_INFO

Содержит сведения о пути поиска символов, которые после состоянии.

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

## <a name="parameters"></a>Параметры

`dwValidFields`

Сочетание флагов из [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) перечисления, указывающее, какой тип поиска сведения, описанные в этой структуре.

`bstrVerboseSearchInfo`

Пути поиска и результаты объединяются в одну строку.

## <a name="remarks"></a>Примечания

Эта структура возвращается из вызова [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) метод.

Если `bstrVerboseSearchInfo` поле не пусто, то он содержит список пути поиска и результаты поиска. Список форматируется с путем, последующим многоточием («...»), а затем результат. Если имеется несколько пар результирующий путь, каждая пара отделяется пару «\r\n» (каретки возврата и перевода строки). Шаблон выглядит следующим образом:

\<path>...\<result>\r\n\<path>...\<result>\r\n\<path>...\<result>

Обратите внимание, что последний элемент последовательности \r\n.

Вот возможного `bstrVerboseSearchInfo` строки, который был отправлен на стандартный выход.

`c:\symbols\user32.pdb... File not found.`

`c:\winnt\symbols\user32.pdb... Version does not match.`

`\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`

## <a name="requirements"></a>Требования

Header: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также

- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)
---
title: MODULE_SYMBOL_SEARCH_INFO Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords:
- MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5f15587759c4f665d1593d1298c47459a0e64aac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714242"
---
# <a name="module_symbol_search_info"></a>MODULE_SYMBOL_SEARCH_INFO

Содержит информацию о состоянии поиска символов, которые были поиск.

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

## <a name="members"></a>Участники

`dwValidFields`\
Комбинация флагов из [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) перечисления с указанием вида поисковой информации, описанной в этой структуре.

`bstrVerboseSearchInfo`\
Путь поиска и результаты скатированы в одну строку.

## <a name="remarks"></a>Примечания

Эта структура возвращается из вызова в метод [GetSymbolInfo.](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)

Если `bstrVerboseSearchInfo` поле не пусто, то оно содержит список поисковых путей и результаты этого поиска. Список отформатирован с помощью пути, за которым следует эллипсис ("..."), за которым следует результат. Если есть более чем одна пара результатов пути, то каждая пара отделяется парой «Зран» (перевозка-возврат/линия). Шаблон выглядит следующим образом:

\<путь>... \<результат>\<> пути... \<результат>\<пути>... \<результат>

Обратите внимание, что последняя запись не имеет последовательности крюн.

Вот возможная `bstrVerboseSearchInfo` строка, которая была отправлена в стандарт из.

`c:\symbols\user32.pdb... File not found.`

`c:\winnt\symbols\user32.pdb... Version does not match.`

`\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`

## <a name="requirements"></a>Требования

Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также

- [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)

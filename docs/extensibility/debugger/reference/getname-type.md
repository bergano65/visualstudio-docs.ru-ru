---
title: GETNAME_TYPE Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- GETNAME_TYPE
helpviewer_keywords:
- GETNAME_TYPE enumeration
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1d0d146ec4ed7340bde36b298df9d455257b35fe
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736670"
---
# <a name="getname_type"></a>GETNAME_TYPE
Упогоняет тип имен файлов для извлечения.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_GETNAME_TYPE {
    GN_NAME         = 0,
    GN_FILENAME     = 1,
    GN_BASENAME     = 2,
    GN_MONIKERNAME  = 3,
    GN_URL          = 4,
    GN_TITLE        = 5,
    GN_STARTPAGEURL = 6
};
typedef DWORD GETNAME_TYPE;
```

```csharp
public enum enum_GETNAME_TYPE {
    GN_NAME         = 0,
    GN_FILENAME     = 1,
    GN_BASENAME     = 2,
    GN_MONIKERNAME  = 3,
    GN_URL          = 4,
    GN_TITLE        = 5,
    GN_STARTPAGEURL = 6
};
```

## <a name="fields"></a>Поля
`GN_NAME`\
Упоняет дружественное название документа или контекста.

`GN_FILENAME`\
Осведён полный путь документа или контекста.

`GN_BASENAME`\
Уотеляет имя базового файла вместо полного пути документа или контекста.

`GN_MONIKERNAME`\
Упоняет уникальное название документа или контекста в виде кличка.

`GN_URL`\
Укажите имя URL документа или контекста.

`GN_TITLE`\
Учтите название документа, если он существует.

`GN_STARTPAGEURL`\
Получает URL-адрес стартовой страницы для процессов.

## <a name="remarks"></a>Примечания
Эти значения передаются в качестве параметров методам [GetName,](../../../extensibility/debugger/reference/idebugdocument2-getname.md) [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)и [GetName,](../../../extensibility/debugger/reference/idebugprocess2-getname.md) чтобы указать, какое имя вернуть.

## <a name="requirements"></a>Требования
Заголовок: msdbg.h

Название: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)
- [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)

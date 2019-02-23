---
title: GETNAME_TYPE | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- GETNAME_TYPE
helpviewer_keywords:
- GETNAME_TYPE enumeration
ms.assetid: 2f9f1679-e9e8-4c9c-ac90-aa07bfe69914
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ae68c77e2d6a41adfff6b49e55bbc6df4393fec7
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56701723"
---
# <a name="getnametype"></a>GETNAME_TYPE
Задает имя тип файлов для извлечения.

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

## <a name="members"></a>Участники
GN_NAME указывает понятное имя документа или контекста.

GN_FILENAME указывает полный путь документа или контекста.

GN_BASENAME указывает имя базового файла, а не полный путь документа или контекста.

GN_MONIKERNAME указывает уникальное имя документа или контекста в виде моникер.

URL-адрес GN_URL имя документа или контекста.

GN_TITLE указывает название документа, если он существует.

Обрабатывает GN_STARTPAGEURL Возвращает начальный URL-адрес для "страницы".

## <a name="remarks"></a>Примечания
Эти значения передаются как параметры для [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md), [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md), и [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md) методы, чтобы указать, какие имени для возврата.

## <a name="requirements"></a>Требования
Header: msdbg.h

Пространство имен: Microsoft.VisualStudio.Debugger.Interop

Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)
- [GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)
- [GetName](../../../extensibility/debugger/reference/idebugprocess2-getname.md)

---
title: SEEK_START | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SEEK_START
helpviewer_keywords:
- SEEK_START enumeration
ms.assetid: 55bd8901-626e-428b-a263-23b14417f4c6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: de4aa0214ab97c330ddfb689076a2c378c4d227a
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66329300"
---
# <a name="seekstart"></a>SEEK_START
Задает положение, с которого следует начать поиск в потоке Дизассемблированный код.

## <a name="syntax"></a>Синтаксис

```cpp
enum enum_SEEK_START { 
   SEEK_START_BEGIN       = 0x0001,
   SEEK_START_END         = 0x0002,
   SEEK_START_CURRENT     = 0x0003,
   SEEK_START_CODECONTEXT = 0x0004,
   SEEK_START_CODELOCID   = 0x0005
};
typedef DWORD SEEK_START;
```

```csharp
public enum enum_SEEK_START { 
   SEEK_START_BEGIN       = 0x0001,
   SEEK_START_END         = 0x0002,
   SEEK_START_CURRENT     = 0x0003,
   SEEK_START_CODECONTEXT = 0x0004,
   SEEK_START_CODELOCID   = 0x0005
};
```

## <a name="fields"></a>Поля
 `SEEK_START_BEGIN`\
 Начинает поиск с начала текущего документа.

 `SEEK_START_END`\
 Начинает поиск в конце текущего документа.

 `SEEK_START_CURRENT`\
 Начинает поиск в текущей позиции текущего документа.

 `SEEK_START_CODECONTEXT`\
 Начинает поиск в контексте данного кода текущего документа.

 `SEEK_START_CODELOCID`\
 Начинает поиск в расположение идентификатора данного кода. Идентификаторы расположение кода можно получить путем вызова [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md).

## <a name="remarks"></a>Примечания
 Передается в качестве аргумента для [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md) метод.

## <a name="requirements"></a>Требования
 Header: msdbg.h

 Пространство имен: Microsoft.VisualStudio.Debugger.Interop

 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>См. также
- [Перечисления](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)
- [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)
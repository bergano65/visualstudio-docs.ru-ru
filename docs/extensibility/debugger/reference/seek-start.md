---
title: SEEK_START | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SEEK_START
helpviewer_keywords:
- SEEK_START enumeration
ms.assetid: 55bd8901-626e-428b-a263-23b14417f4c6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e003b74faeb7c6ed165c43380a7c4c6b0520ea0c
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56677999"
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

## <a name="members"></a>Участники
 SEEK_START_BEGIN начинает поиск с начала текущего документа.

 SEEK_START_END начинает поиск в конце текущего документа.

 SEEK_START_CURRENT начинает поиск в текущей позиции текущего документа.

 SEEK_START_CODECONTEXT начинает поиск в контексте данного кода текущего документа.

 SEEK_START_CODELOCID начинает поиск в расположение идентификатора данного кода. Идентификаторы расположение кода можно получить путем вызова [GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md).

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
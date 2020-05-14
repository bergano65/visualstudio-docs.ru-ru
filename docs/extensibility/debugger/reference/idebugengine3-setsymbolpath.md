---
title: IDebugEngine3::SetSymbolPath Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetSymbolPath
helpviewer_keywords:
- IDebugEngine3::SetSymbolPath
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1fbe5128900fa10147c747cbcba4129e96d4c4ce
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730661"
---
# <a name="idebugengine3setsymbolpath"></a>IDebugEngine3::SetSymbolPath
Устанавливает путь или пути, которые ищутдля для отладки символов.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetSymbolPath (
   LPOLESTR            szSymbolSearchPath,
   LPOLESTR            szSymbolCachePath,
   LOAD_SYMBOLS_FLAGS  Flags
);
```

```csharp
int SetSymbolPath(
   string                    szSymbolSearchPath,
   string                    szSymbolCachePath,
   enum_LOAD_SYMBOLS_FLAGS   Flags
);
```

## <a name="parameters"></a>Параметры

`szSymbolSearchPath`\
(в) Строка, содержащая путь поиска символов или пути. Подробности смотрите в материале "Замечания". Не может иметь значение null.

`szSymbolCachePath`\
(в) Строка, содержащая локальный путь, по которому символы могут быть кэшированы. Не может иметь значение null.

`Flags`\
(в) Не используется; всегда устанавливается на 0.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращается S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Строка `szSymbolSearchPath` представляет собой список одного или нескольких путей, разделенных запятых, для поиска символов. Эти пути могут быть локальным путем, пути в стиле КООН или URL-адреса. Эти пути также могут быть смесью различных типов. Если путь является КООН (например, \\«Символы Symserver»), то движок отладки должен определить, является ли путь к серверу символов и должен быть в состоянии загрузить символы с этого сервера, кэширование их в пути, указанном `szSymbolCachePath`.

 Путь символа также может содержать одно или несколько мест кэша. Кэши перечислены в порядке приоритета, сначала кэш с наивысшим приоритетом и разделены символами. Пример:

```
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*https://msdl.microsoft.com
```

 Метод [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) выполняет фактическую нагрузку символов.

## <a name="see-also"></a>См. также
- [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)

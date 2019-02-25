---
title: IDebugEngine3::LoadSymbols | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::LoadSymbols
helpviewer_keywords:
- IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff317b217b72fcb5a6042747abd88e5a9d344f7a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56681274"
---
# <a name="idebugengine3loadsymbols"></a>IDebugEngine3::LoadSymbols
Загружает (при необходимости) символы для всех модулей, отладку этого ядро отладки.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT LoadSymbols();
```

```csharp
int LoadSymbols();
```

#### <a name="parameters"></a>Параметры
 Отсутствует.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Это загружает отладочные символы для всех модулей, которые ссылается это ядро отладки. Символы загружаются только в том случае, если они еще не загружен. Символы производится поиск по путям, заданный вызовом к [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md).

## <a name="see-also"></a>См. также
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
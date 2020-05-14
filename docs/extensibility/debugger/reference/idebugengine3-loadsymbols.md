---
title: IDebugEngine3::LoadSymbols Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::LoadSymbols
helpviewer_keywords:
- IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7963d39601a0d3a90ca2daa7632902d7aa506de8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730812"
---
# <a name="idebugengine3loadsymbols"></a>IDebugEngine3::LoadSymbols
Загружает (по мере необходимости) символы для всех модулей, отлаженных этим двигателем отладки.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT LoadSymbols();
```

```csharp
int LoadSymbols();
```

## <a name="parameters"></a>Параметры
 Нет.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха, возвращается S_OK; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Это нагрузок отладки символов для всех модулей, упомянутых этой отладки двигателя. Символы загружаются только в том случае, если они еще не загружены. Символы ищутся на путях, установленных вызовом [на SetSymbolPath.](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)

## <a name="see-also"></a>См. также
- [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)

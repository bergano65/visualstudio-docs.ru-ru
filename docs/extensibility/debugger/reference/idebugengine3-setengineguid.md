---
title: 'IDebugEngine3:: Сетенгинегуид | Документация Майкрософт'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine3::SetEngineGuid
helpviewer_keywords:
- IDebugEngine3::SetEngineGuid
ms.assetid: 8bdfa05d-feb7-4d98-abac-77825a04c50f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2aaf50076978d5a6d4562eddf54de4651b3c6410
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887215"
---
# <a name="idebugengine3setengineguid"></a>IDebugEngine3::SetEngineGuid
Этот метод задает для модуля отладки (DE) `GUID` .

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetEngineGuid(
   GUID* guidEngine
);
```

```csharp
int SetEngineGuid(
   ref Guid guidEngine
);
```

## <a name="parameters"></a>Параметры
`guidEngine`\
[входные] `GUID` подсистемы.

## <a name="return-value"></a>Возвращаемое значение
 В случае успеха возвращает `S_OK` ; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также раздел
- [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)

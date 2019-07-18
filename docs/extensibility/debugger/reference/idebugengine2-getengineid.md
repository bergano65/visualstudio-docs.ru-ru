---
title: IDebugEngine2::GetEngineID | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::GetEngineID
helpviewer_keywords:
- IDebugEngine2::GetEngineID
ms.assetid: 0d5674c8-a9b9-4b72-8211-d2d68695775a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 29b6f219447e3c58bce9f5b4696697163ab4f6a1
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66318471"
---
# <a name="idebugengine2getengineid"></a>IDebugEngine2::GetEngineID
Получает идентификатор GUID модуля отладки (DE).

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetEngineID(
    GUID* pguidEngine
);
```

```csharp
int GetEngineID(
    out Guid pguidEngine
);
```

## <a name="parameters"></a>Параметры
`pguidEngine`\
[out] Возвращает идентификатор GUID DE.

## <a name="return-value"></a>Возвращаемое значение
В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
Некоторые примеры типичных GUID: `guidScriptEng`, `guidNativeEng`, или `guidSQLEng`. Новый отладчиков создаст собственные GUID для идентификации.

## <a name="example"></a>Пример
В следующем примере показано, как реализовать этот метод для простого `CEngine` объект, реализующий [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md) интерфейс.

```cpp
HRESULT CEngine::GetEngineId(GUID *pguidEngine) {
    if (pguidEngine) {
        // Set pguidEngine to guidBatEng, as defined in the Batdbg.idl file.
        // Other languages would require their own guidDifferentEngine to be
        //defined in the Batdbg.idl file.
        *pguidEngine = guidBatEng;
        return NOERROR; // This is typically S_OK.
    } else {
        return E_INVALIDARG;
    }
}
```

## <a name="see-also"></a>См. также
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)

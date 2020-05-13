---
title: IDebugПрограмма2::GetProcess Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetProcess
helpviewer_keywords:
- IDebugProgram2::GetProcess
ms.assetid: 1d602485-ebaf-451c-9165-f2e226f20a90
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aca1842e92e7e1c164a6468e6c1e94a352ef67c0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722792"
---
# <a name="idebugprogram2getprocess"></a>IDebugProgram2::GetProcess
Получите процесс, в который работает эта программа.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetProcess(
   IDebugProcess2** ppProcess
);
```

```csharp
int GetProcess(
   out IDebugProcess2 ppProcess
);
```

## <a name="parameters"></a>Параметры
`ppProcess`\
(ваут) Возвращает интерфейс [IDebugProcess2,](../../../extensibility/debugger/reference/idebugprocess2.md) представляющий процесс.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Если отладка двигателя (DE) реализует интерфейс [IDebugEngineLaunch2,](../../../extensibility/debugger/reference/idebugenginelaunch2.md) реализация DE этого `E_NOTIMPL` метода всегда должна вернуться, потому что DE не может определить, в каком процессе он работает, и поэтому не может удовлетворить реализацию этого метода.

 Реализация интерфейса `IDebugEngineLaunch2` означает, что DE должен знать, как создать процесс; Таким образом, реализация интерфейса [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) для DE способна знать, в каком процессе он работает.

## <a name="see-also"></a>См. также
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)

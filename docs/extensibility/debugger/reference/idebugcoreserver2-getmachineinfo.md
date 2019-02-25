---
title: IDebugCoreServer2::GetMachineInfo | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetInfo
helpviewer_keywords:
- IDebugCoreServer2::GetInfo
ms.assetid: 8fa1a1d3-9fcb-4fb3-bf4e-e7172ac08d77
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c23e399a2debac06df239fe69ced6589d00f7774
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56686318"
---
# <a name="idebugcoreserver2getmachineinfo"></a>IDebugCoreServer2::GetMachineInfo
Возвращает описание core server, запущенного на компьютере.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetMachineInfo( 
   MACHINE_INFO_FIELDS Fields,
   MACHINE_INFO*       pMachineInfo
);
```

```csharp
int GetMachineInfo( 
   enum_ MACHINE_INFO_FIELDS  Fields,
   MACHINE_INFO[]             pMachineInfo
);
```

#### <a name="parameters"></a>Параметры
 `Fields`

 [in] Сочетание флагов из [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md) перечисление, указать, какие поля из `pMachineInfo` , для заполнения.

 `pMachineInfo`

 [in, out] Объект [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) структуры, который заполняется описание машины.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
- [MACHINE_INFO_FIELDS](../../../extensibility/debugger/reference/machine-info-fields.md)
- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)

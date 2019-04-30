---
title: IDebugCoreServer2::GetMachineUtilities_V7 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2929ed704d8b9642d30b9a7951a707db0635b319
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63414043"
---
# <a name="idebugcoreserver2getmachineutilitiesv7"></a>IDebugCoreServer2::GetMachineUtilities_V7
Этот метод возвращает машины служебные программы для сервера.

> [!NOTE]
> Этот метод является устаревшим: не используйте ([!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] всегда возвращает `E_NOTIMPL` при вызове этого метода). Он сохраняется по историческим причинам.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetMachineUtilities_V7(
   IDebugMDMUtil2_V7** ppUtil
);
```

```csharp
int GetMachineUtilities_V7(
   out IDebugMDMUtil2_V7 ppUtil
);
```

#### <a name="parameters"></a>Параметры
 `ppUtil`

 [out] Возвращает `IDebugMDMUtil2_V7` интерфейс, который представляет сведения о машине служебные программы.

## <a name="return-value"></a>Возвращаемое значение
 Всегда возвращает `E_NOTIMPL`, указывающее, что метод не реализован.

## <a name="remarks"></a>Примечания
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] всегда возвращает `E_NOTIMPL` при вызове этого метода.

## <a name="see-also"></a>См. также
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
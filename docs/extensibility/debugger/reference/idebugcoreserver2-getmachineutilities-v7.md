---
title: IDebugCoreServer2::GetMachineUtilities_V7 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c5aefe3b348f36b32792ebce9600f846d5a9cffe
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66317833"
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

## <a name="parameters"></a>Параметры
`ppUtil`\
[out] Возвращает `IDebugMDMUtil2_V7` интерфейс, который представляет сведения о машине служебные программы.

## <a name="return-value"></a>Возвращаемое значение
 Всегда возвращает `E_NOTIMPL`, указывающее, что метод не реализован.

## <a name="remarks"></a>Примечания
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] всегда возвращает `E_NOTIMPL` при вызове этого метода.

## <a name="see-also"></a>См. также
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
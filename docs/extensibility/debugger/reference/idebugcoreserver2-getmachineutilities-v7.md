---
title: IDebugCoreServer2::GetMachineUtilities_V7 Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 79eba6889583f1dfa482dab107ad31eaaacdbcc2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733153"
---
# <a name="idebugcoreserver2getmachineutilities_v7"></a>IDebugCoreServer2::GetMachineUtilities_V7
Этот метод получает утилиты машины для сервера.

> [!NOTE]
> Этот метод устарел: не[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] используйте `E_NOTIMPL` (всегда возвращается, если этот метод называется). Он сохраняется по историческим причинам.

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
(ваут) Возвращает `IDebugMDMUtil2_V7` интерфейс, представляющий информацию о утилитах машины.

## <a name="return-value"></a>Возвращаемое значение
 Всегда `E_NOTIMPL`возвращается, указывая, что метод не реализован.

## <a name="remarks"></a>Примечания
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]всегда `E_NOTIMPL` возвращается, если этот метод называется.

## <a name="see-also"></a>См. также
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)

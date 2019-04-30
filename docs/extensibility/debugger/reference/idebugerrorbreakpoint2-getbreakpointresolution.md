---
title: IDebugErrorBreakpoint2::GetBreakpointResolution | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugErrorBreakpoint2::GetBreakpointResolution
helpviewer_keywords:
- IDebugErrorBreakpoint2::GetBreakpointResolution
ms.assetid: 1c2324ed-2a11-4e63-8f3a-f420c7a4018b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1b1ba346a24c22a01039736b53568a89684af92c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62874731"
---
# <a name="idebugerrorbreakpoint2getbreakpointresolution"></a>IDebugErrorBreakpoint2::GetBreakpointResolution
Получает значение разрешения ошибки точки останова с описанием ошибки.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetBreakpointResolution( 
   IDebugErrorBreakpointResolution2** ppErrorResolution
);
```

```csharp
int GetBreakpointResolution( 
   out IDebugErrorBreakpointResolution2 ppErrorResolution
);
```

#### <a name="parameters"></a>Параметры
 `ppErrorResolution`

 [out] Возвращает [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md) , описывающий ошибку.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
- [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)
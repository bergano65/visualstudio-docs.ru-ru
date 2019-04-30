---
title: IEEVisualizerService::GetValueDisplayStringCount | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IEEVisualizerService::GetValueDisplayStringCount
- GetValueDisplayStringCount
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b3ed52e8be77e5f4dce081fc6a60ae22cecbb990
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62915200"
---
# <a name="ieevisualizerservicegetvaluedisplaystringcount"></a>IEEVisualizerService::GetValueDisplayStringCount
Возвращает номер строки значение указанного свойства или поля.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetValueDisplayStringCount (
   DWORD         displayKind,
   IDebugField * propertyOrField,
   ULONG *       pcelt
);
```

```csharp
int GetValueDisplayStringCount (
   uint        displayKind,
   IDebugField propertyOrField,
   out ulong   pcelt
);
```

#### <a name="parameters"></a>Параметры
 `displayKind`

 [in] Значение из [DisplayKind](../../../extensibility/debugger/reference/displaykind.md) перечисления.

 `propertyOrField`

 [in] [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) интерфейс, который представляет свойство или поле.

 `pcelt`

 [out] Возвращает число строк, значение для отображения.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
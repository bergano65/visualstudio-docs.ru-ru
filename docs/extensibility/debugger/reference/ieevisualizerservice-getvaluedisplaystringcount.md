---
title: IEEVisualizerService::GetValueDisplayStringCount Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IEEVisualizerService::GetValueDisplayStringCount
- GetValueDisplayStringCount
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5c1a664594e55b8db21562a650c2c750668c2584
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717989"
---
# <a name="ieevisualizerservicegetvaluedisplaystringcount"></a>IEEVisualizerService::GetValueDisplayStringCount
Извлекает количество строк значения для отображения для указанного свойства или поля.

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

## <a name="parameters"></a>Параметры
`displayKind`\
(в) Значение из перечисления [DisplayKind.](../../../extensibility/debugger/reference/displaykind.md)

`propertyOrField`\
(в) Интерфейс [IDebugField,](../../../extensibility/debugger/reference/idebugfield.md) представляющий свойство или поле.

`pcelt`\
(ваут) Возвращает количество строк значения для отображения.

## <a name="return-value"></a>Возвращаемое значение
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)

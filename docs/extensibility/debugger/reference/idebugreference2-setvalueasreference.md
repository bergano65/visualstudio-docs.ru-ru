---
title: IDebugСправка2::SetvalueAsСправка (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::SetValueAsReference
helpviewer_keywords:
- IDebugReference2::SetValueAsReference
ms.assetid: 94a545d2-16b9-45e9-b2e7-4e49ff90aad0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f4767dbe08e716d64ea03c18a1c4a6f7d6690a7b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720305"
---
# <a name="idebugreference2setvalueasreference"></a>IDebugReference2::SetValueAsReference
Устанавливает значение ссылки из другой ссылки. Зарезервировано для последующего использования.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetValueAsReference ( 
   IDebugReference2** rgpArgs,
   DWORD              dwArgCount,
   IDebugReference2*  pValue,
   DWORD              dwTimeout
);
```

```cpp
int SetValueAsReference ( 
   IDebugReference2[] rgpArgs,
   uint               dwArgCount,
   IDebugReference2   pValue,
   uint               dwTimeout
);
```

## <a name="parameters"></a>Параметры
`rgpArgs`\
(в) Массив объектов [IDebugReference2,](../../../extensibility/debugger/reference/idebugreference2.md) используемых для определения эталонного значения.

`dwArgCount`\
(в) Количество ссылок в массиве.

`pValue`\
(в) Объект [IDebugReference2,](../../../extensibility/debugger/reference/idebugreference2.md) с которого можно установить значение свойства.

`dwTimeout`\
(в) Максимальное время, в миллисекундах, ждать, прежде чем вернуться из этого метода. Используйте, `INFINITE` чтобы ждать бесконечно.

## <a name="return-value"></a>Возвращаемое значение
 Всегда возвращает значение `E_NOTIMPL`.

## <a name="see-also"></a>См. также
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)

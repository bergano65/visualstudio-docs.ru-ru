---
title: IDebugReference2::SetValueAsReference | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::SetValueAsReference
helpviewer_keywords:
- IDebugReference2::SetValueAsReference
ms.assetid: 94a545d2-16b9-45e9-b2e7-4e49ff90aad0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2b14ca1293a709dce35f2e8aa45a7fa22bf29845
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68178187"
---
# <a name="idebugreference2setvalueasreference"></a>IDebugReference2::SetValueAsReference
Задает значение ссылки из другой ссылки. Зарезервировано для будущего использования.

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

#### <a name="parameters"></a>Параметры
 `rgpArgs`

 [in] Массив [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) объектов, используемых для определения способа установки значения ссылки.

 `dwArgCount`

 [in] Количество ссылок в массиве.

 `pValue`

 [in] [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) объект, из которого требуется задать значение свойства.

 `dwTimeout`

 [in] Максимальное время в миллисекундах для ожидания перед возвратом из этого метода. Используйте `INFINITE` для неограниченного времени ожидания.

## <a name="return-value"></a>Возвращаемое значение
 Всегда возвращает значение `E_NOTIMPL`.

## <a name="see-also"></a>См. также
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
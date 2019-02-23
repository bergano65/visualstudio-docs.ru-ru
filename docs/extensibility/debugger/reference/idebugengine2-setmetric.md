---
title: IDebugEngine2::SetMetric | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2:::SetMetric
helpviewer_keywords:
- IDebugEngine2:::SetMetric
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 325cd30a49fb636c56eebd9e6301b3999e851363
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56713611"
---
# <a name="idebugengine2setmetric"></a>IDebugEngine2::SetMetric
Этот метод задает значение реестра, известный как метрики.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT SetMetric(
   LPCOLESTR pszMetric,
   VARIANT   varValue
);
```

```csharp
int SetMetric(
   string pszMetric,
   object varValue
);
```

#### <a name="parameters"></a>Параметры
 `pszMetric`

 [in] Имя метрики.

 `varValue`

 [in] Указывает значение метрики.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="remarks"></a>Примечания
 Метрика — это значение реестра, чтобы изменить поведение модуля отладки или для объявления поддерживаемые функции. Этот метод можно пересылать подходящей формой [вспомогательные пакеты SDK для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) функции `SetMetric`.

## <a name="see-also"></a>См. также
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [Вспомогательные пакеты SDK для отладки](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)
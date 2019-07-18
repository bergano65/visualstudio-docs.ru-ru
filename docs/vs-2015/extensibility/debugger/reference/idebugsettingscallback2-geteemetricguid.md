---
title: IDebugSettingsCallback2::GetEEMetricGuid | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricGuid
ms.assetid: 3d70c19a-595d-44f1-a7b3-a0cf8f15e371
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b1cf70c424856b93eb4d082a167bc671b885a346
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68155193"
---
# <a name="idebugsettingscallback2geteemetricguid"></a>IDebugSettingsCallback2::GetEEMetricGuid
Извлекает уникальный идентификатор для метрики вычислителя выражения, заданную ее именем.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetEEMetricGuid(
   REFGUID guidLang,
   REFGUID guidVendor,
   LPCWSTR pszMetric,
   GUID*   pguidValue
);
```

```csharp
HRESULT GetEEMetricGuid(
   ref Guid guidLang,
   ref Guid guidVendor,
   string   pszMetric,
   out Guid pguidValue
);
```

#### <a name="parameters"></a>Параметры
 `guidLang`

 [in] Уникальный идентификатор языка программирования.

 `guidVendor`

 [in] Уникальный идентификатор поставщика.

 `pszMetric`

 [in] Имя метрики.

 `pguidValue`

 [out] Возвращает уникальный идентификатор метрики.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)
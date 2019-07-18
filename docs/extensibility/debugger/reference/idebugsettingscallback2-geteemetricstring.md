---
title: IDebugSettingsCallback2::GetEEMetricString | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricString
ms.assetid: 85e3c093-6a91-4101-ab32-d8ac6eed4918
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: cd4ac00a03204ac9104ea965145874ac950f7304
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322091"
---
# <a name="idebugsettingscallback2geteemetricstring"></a>IDebugSettingsCallback2::GetEEMetricString
Извлекает строковое значение метрики вычислителя выражений, заданную ее именем.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetEEMetricString(
   REFGUID guidLang,
   REFGUID guidVendor,
   LPCWSTR pszMetric,
   BSTR*   pbstrValue
);
```

```csharp
private int GetEEMetricString(
   ref Guid   guidLang,
   ref Guid   guidVendor,
   string     pszMetric,
   out string pbstrValue
);
```

## <a name="parameters"></a>Параметры
`guidLang`\
[in] Уникальный идентификатор языка программирования.

`guidVendor`\
[in] Уникальный идентификатор поставщика.

`pszMetric`\
[in] Имя метрики.

`pbstrValue`\
[out] Возвращает строковое значение метрики.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)
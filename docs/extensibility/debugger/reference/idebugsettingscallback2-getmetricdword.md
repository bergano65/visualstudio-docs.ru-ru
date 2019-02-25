---
title: IDebugSettingsCallback2::GetMetricDword | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetMetricDword
ms.assetid: 831a5a1a-c4af-4520-9fdf-3a731aeff85c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 85451229b9b34f63150b315521621368c60cb1ac
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/22/2019
ms.locfileid: "56697667"
---
# <a name="idebugsettingscallback2getmetricdword"></a>IDebugSettingsCallback2::GetMetricDword
Извлекает значение метрики, заданную ее именем.

## <a name="syntax"></a>Синтаксис

```cpp
HRESULT GetMetricDword(
   LPCWSTR pszType,
   REFGUID guidSection,
   LPCWSTR pszMetric,
   DWORD*  pdwValue
);
```

```csharp
private int GetMetricDword(
   string   pszType,
   ref Guid guidSection,
   string   pszMetric,
   out uint pdwValue
);
```

#### <a name="parameters"></a>Параметры
 `pszType`

 [in] Тип метрики.

 `guidSection`

 [in] Уникальный идентификатор раздела.

 `pszMetric`

 [in] Имя метрики.

 `pdwValue`

 [out] Возвращает значение метрики.

## <a name="return-value"></a>Возвращаемое значение
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.

## <a name="see-also"></a>См. также
- [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)
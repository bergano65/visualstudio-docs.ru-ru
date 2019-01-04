---
title: IDebugSettingsCallback2::GetEEMetricDword | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricDword
ms.assetid: c5f8f417-0ef0-4fd0-a779-b0a8ead4effe
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: baec613bf899f432ca9859aba70a2018fdc9d2e2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53854377"
---
# <a name="idebugsettingscallback2geteemetricdword"></a>IDebugSettingsCallback2::GetEEMetricDword
Извлекает значение, соответствующее заданной метрики средство оценки выражений.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetEEMetricDword(  
   REFGUID guidLang,  
   REFGUID guidVendor,  
   LPCWSTR pszMetric,  
   DWORD*  pdwValue  
);  
```  
  
```csharp  
private int GetEEMetricDword(  
   ref Guid guidLang,  
   ref Guid guidVendor,  
   string   pszMetric,  
   out uint pdwValue  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `guidLang`  
 [in] Уникальный идентификатор языка программирования.  
  
 `guidVendor`  
 [in] Уникальный идентификатор поставщика.  
  
 `pszMetric`  
 [in] Имя метрики.  
  
 `pdwValue`  
 [out] Возвращает значение, соответствующее строке метрик.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)
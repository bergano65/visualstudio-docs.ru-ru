---
title: IDebugSettingsCallback2::GetEEMetricDword | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricDword
ms.assetid: c5f8f417-0ef0-4fd0-a779-b0a8ead4effe
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 475a2a22e148c1b2849d469889492f7eb271e7e1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62868996"
---
# <a name="idebugsettingscallback2geteemetricdword"></a>IDebugSettingsCallback2::GetEEMetricDword
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Извлекает значение, соответствующее заданной метрики средство оценки выражений.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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

---
title: IDebugSettingsCallback2::GetEEMetricGuid | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricGuid
ms.assetid: 3d70c19a-595d-44f1-a7b3-a0cf8f15e371
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 22fab6f0754b212e7df13ea8e6809b83673376a7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49870099"
---
# <a name="idebugsettingscallback2geteemetricguid"></a>IDebugSettingsCallback2::GetEEMetricGuid
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Извлекает уникальный идентификатор для метрики вычислителя выражения, заданную ее именем.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)


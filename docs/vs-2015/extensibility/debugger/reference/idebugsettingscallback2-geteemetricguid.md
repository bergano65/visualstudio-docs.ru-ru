---
title: 'IDebugSettingsCallback2:: Жетиметрикгуид | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugSettingsCallback2::GetEEMetricGuid
ms.assetid: 3d70c19a-595d-44f1-a7b3-a0cf8f15e371
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b1cf70c424856b93eb4d082a167bc671b885a346
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155193"
---
# <a name="idebugsettingscallback2geteemetricguid"></a>IDebugSettingsCallback2::GetEEMetricGuid
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает уникальный идентификатор для метрики средства оценки выражений по заданному имени.  
  
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
 окне Уникальный идентификатор языка программирования.  
  
 `guidVendor`  
 окне Уникальный идентификатор поставщика.  
  
 `pszMetric`  
 окне Имя метрики.  
  
 `pguidValue`  
 заполняет Возвращает уникальный идентификатор метрики.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)

---
title: IDebugSettingsCallback2::GetMetricDword | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugSettingsCallback2::GetMetricDword
ms.assetid: 831a5a1a-c4af-4520-9fdf-3a731aeff85c
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 99b1528c6036f3548ce6b5af3db48764731197f0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558659"
---
# <a name="idebugsettingscallback2getmetricdword"></a>IDebugSettingsCallback2::GetMetricDword
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugSettingsCallback2::GetMetricDword](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugsettingscallback2-getmetricdword).  
  
Извлекает значение метрики, заданную ее именем.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md)


---
title: IDebugBinder3::GetEEService | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugBinder3::GetEEService
helpviewer_keywords:
- IDebugBinder3::GetEEService method
ms.assetid: eb07aa40-8cd9-4a52-a4c7-4affd2307a01
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2b0739294f5c2b003baa7e221c7e617456fda89e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53822046"
---
# <a name="idebugbinder3geteeservice"></a>IDebugBinder3::GetEEService
Этот метод возвращает запрошенную службу.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetEEService(  
   [in] GUID        vendor,  
   [in] GUID        language,  
   [in] GUID        iid,  
   [out] IUnknown** ppService  
);  
```  
  
```csharp  
Int GetEEService(  
   Guid       vendor,  
   Guid       language,  
   Guid       iid,  
   out object ppService  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `vendor`  
 [in] `GUID` поставщика (допустимо значение null).  
  
 `language`  
 [in] `GUID` языка (допустимо значение null).  
  
 `iid`  
 [in] `IID` службы для получения.  
  
 `ppService`  
 [out] Интерфейс запрошенную службу.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Передайте `IID` для [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md) интерфейс (`IID_IEEVisualizerServiceProvider`) для получения сведений о службе типа визуализатора. Если таким образом, можно получить средство оценки выражений [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md) интерфейс для поддержки визуализаторами типов. См. в разделе [визуализация и просмотр данных](../../../extensibility/debugger/visualizing-and-viewing-data.md) подробные сведения.  
  
## <a name="see-also"></a>См. также  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [Визуализация и просмотр данных](../../../extensibility/debugger/visualizing-and-viewing-data.md)
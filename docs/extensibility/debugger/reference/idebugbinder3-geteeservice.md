---
title: IDebugBinder3::GetEEService | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
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
ms.openlocfilehash: 5b283ecf3a21f5a5b9246a628a959b4a271c884b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49866666"
---
# <a name="idebugbinder3geteeservice"></a>IDebugBinder3::GetEEService
Этот метод возвращает запрошенную службу.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetEEService(  
   [in] GUID        vendor,  
   [in] GUID        language,  
   [in] GUID        iid,  
   [out] IUnknown** ppService  
);  
```  
  
```csharp  
Int GetEEService(  
   Guid       vendor,  
   Guid       language,  
   Guid       iid,  
   out object ppService  
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
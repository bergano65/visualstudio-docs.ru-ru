---
title: IEEVisualizerService::GetCustomViewerList | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEEVisualizerService::GetCustomViewerList
helpviewer_keywords:
- IEEVisualizerService::GetCustomViewerList method
ms.assetid: 249d26ca-914f-43af-a400-8162477223f4
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e037ac728c47b2b4610d866b2ba3868dc44b4eb0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47557518"
---
# <a name="ieevisualizerservicegetcustomviewerlist"></a>IEEVisualizerService::GetCustomViewerList
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IEEVisualizerService::GetCustomViewerList](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist).  
  
Этот метод возвращает список визуализаторов типов, эта служба, о которых известно.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetCustomViewerList(  
   ULONG                celtSkip,  
   ULONG                celtRequested,  
   DEBUG_CUSTOM_VIEWER* rgViewers,  
   ULONG*               pceltFetched  
);  
```  
  
```csharp  
int GetCustomViewerList(  
   uint                  celtSkip,  
   uint                  celtRequested,  
   DEBUG_CUSTOM_VIEWER[] rgViewers,  
   out uint              pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `celtSkip`  
 [in] Число визуализаторы для пропуска.  
  
 `celRequested`  
 [in] Число визуализаторы для извлечения (также указывает размер `rgViewers` массива).  
  
 `rgViewers`  
 [in, out] Массив [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) структур для заполнения.  
  
 `pceltFetched`  
 [out] Число фактически извлеченных визуализаторы.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) передает запрос в этот метод как часть поддержки для визуализаторов типов. Если средство оценки выражений также поддерживает пользовательские средства просмотра для одного типа, оно может Дописывать соответствующим образом заполненную [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) структуры для этих пользовательских средств просмотра, в список. Убедитесь, что [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md) отражает этих дополнительных средств просмотра.  
  
 См. в разделе [визуализатор типов и пользовательские средства просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) Дополнительные сведения о различиях между визуализаторы, а также средства просмотра.  
  
## <a name="see-also"></a>См. также  
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [GetCustomViewerCount](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewercount.md)   
 [Визуализатор типов и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)


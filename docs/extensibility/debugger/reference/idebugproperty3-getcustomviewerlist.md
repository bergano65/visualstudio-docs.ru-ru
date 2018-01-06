---
title: "IDebugProperty3::GetCustomViewerList | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProperty3::GetCustomViewerList
helpviewer_keywords: IDebugProperty3::GetCustomViewerList
ms.assetid: 74490fd8-6f44-4618-beea-dab64961bb8a
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1cd719891b4c0baec4d143c4a848e0c1d31ad6e3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="idebugproperty3getcustomviewerlist"></a>IDebugProperty3::GetCustomViewerList
Получает список пользовательских средств просмотра, связанный с этим свойством.  
  
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
 [in] Число средств просмотра, чтобы перейти к странице.  
  
 `celtRequested`  
 [in] Количество представлений, чтобы получить (также определяет размер `rgViewers` массива).  
  
 `rgViewers`  
 [in, out] Массив [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) структур, которые должны заполняться в.  
  
 `pceltFetched`  
 [out] Возвращает фактическое количество средств просмотра.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Для поддержки визуализаторами типов, этот метод передает вызов [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) метод. Если средство оценки выражений также поддерживает пользовательские средства просмотра для этого свойства типа, этот метод можно добавлять в список соответствующих пользовательских средств просмотра.  
  
 В разделе [тип визуализатора и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) сведения о различиях между визуализаторами типов и пользовательских средств просмотра.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как реализовать этот метод для **CProperty** объекта, который предоставляет [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) интерфейса.  
  
```cpp  
STDMETHODIMP CProperty::GetCustomViewerList(ULONG celtSkip, ULONG celtRequested, DEBUG_CUSTOM_VIEWER* prgViewers, ULONG* pceltFetched)  
{  
    if (NULL == prgViewers)  
    {  
        return E_POINTER;  
    }  
  
    if (GetVisualizerService())  
    {  
        return m_pIEEVisualizerService->GetCustomViewerList(celtSkip, celtRequested, prgViewers, pceltFetched);  
    }  
    else  
    {  
        return E_NOTIMPL;  
    }  
}  
```  
  
## <a name="see-also"></a>См. также  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)   
 [Визуализатор типов и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
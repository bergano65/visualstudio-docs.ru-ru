---
title: "IDebugProperty3::GetCustomViewerList | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty3::GetCustomViewerList"
helpviewer_keywords: 
  - "IDebugProperty3::GetCustomViewerList"
ms.assetid: 74490fd8-6f44-4618-beea-dab64961bb8a
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProperty3::GetCustomViewerList
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Получает список пользовательских средств просмотра, связанных с данным свойством.  
  
## Синтаксис  
  
```cpp  
HRESULT GetCustomViewerList(  
   ULONG                celtSkip,  
   ULONG                celtRequested,  
   DEBUG_CUSTOM_VIEWER* rgViewers,  
   ULONG*               pceltFetched  
);  
```  
  
```c#  
int GetCustomViewerList(  
   uint                  celtSkip,  
   uint                  celtRequested,  
   DEBUG_CUSTOM_VIEWER[] rgViewers,  
   out uint              pceltFetched  
);  
```  
  
#### Параметры  
 `celtSkip`  
 \[in\] число средств просмотра, которые нужно пропустить.  
  
 `celtRequested`  
 \[in\] число извлекаемых \(просмотра также определяет размер `rgViewers` массив\).  
  
 `rgViewers`  
 \[in, out\] массив [DEBUG\_CUSTOM\_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) структуры, которую требуется заполнить.  
  
 `pceltFetched`  
 \[out\] фактическое количество средств просмотра, возвращенных.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Для поддержки визуализаторы типа, этот метод переадресует вызов [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md) метод.  Если средство оценки выражений также поддерживает пользовательских средств просмотра для данного типа свойства, то данный метод может добавить соответствующие пользовательских средствах просмотра в список.  
  
 См. [Тип визуализатора и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md) дополнительные сведения о различиях между пользовательскими визуализаторами типа и телезрителями.  
  
## Пример  
 В следующем примере показано, как реализовать этот метод, a **CProperty** объект, предоставляющий  [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) интерфейс.  
  
```cpp#  
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
  
## См. также  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DEBUG\_CUSTOM\_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewerlist.md)   
 [Тип визуализатора и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)
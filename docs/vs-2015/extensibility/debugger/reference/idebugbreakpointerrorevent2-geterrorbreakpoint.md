---
title: IDebugBreakpointErrorEvent2::GetErrorBreakpoint | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugBreakpointErrorEvent2::GetErrorBreakpoint
helpviewer_keywords:
- IDebugBreakpointErrorEvent2::GetErrorBreakpoint
ms.assetid: e5acfd19-ac17-47f3-a31a-b2aa8baca36d
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eb3920062f9a904f6180a5b4964b02e222da1741
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51761787"
---
# <a name="idebugbreakpointerrorevent2geterrorbreakpoint"></a>IDebugBreakpointErrorEvent2::GetErrorBreakpoint
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Получает [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) , описывающий причину, почему не привязан в точку останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetErrorBreakpoint(   
   IDebugErrorBreakpoint2** ppErrorBP  
);  
```  
  
```csharp  
int GetErrorBreakpoint(   
   out IDebugErrorBreakpoint2 ppErrorBP  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppErrorBP`  
 [out] Возвращает [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) , описывающий предупреждения или ошибки.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 После `IDebugErrorBreakpoint2` интерфейс получается, вызовите [GetBreakpointResolution](../../../extensibility/debugger/reference/idebugerrorbreakpoint2-getbreakpointresolution.md) метод для получения [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md) объекта. Затем [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) метод может использоваться для определения недопустимое расположение, недопустимое выражение точки или причин, почему ожидающая точка останова не привязан, например код, не загружен и т. д.  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как реализовать этот метод для **CBreakpointSetDebugEventBase** объекта, который предоставляет [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) интерфейс.  
  
```cpp#  
STDMETHODIMP CBreakpointErrorDebugEventBase::GetErrorBreakpoint(  
    IDebugErrorBreakpoint2 **ppbp)  
{  
    HRESULT hRes = E_FAIL;  
  
    if ( ppbp )  
    {  
        if ( m_pError )  
        {  
            *ppbp = m_pError;  
  
            m_pError->AddRef();  
  
            hRes = S_OK;  
        }  
        else  
            hRes = E_FAIL;  
    }  
    else  
        hRes = E_INVALIDARG;  
  
    return ( hRes );  
}  
```  
  
## <a name="see-also"></a>См. также  
 [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)   
 [IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)   
 [IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)


---
title: IDebugProperty3::GetCustomViewerCount | Документация Майкрософт
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
- IDebugProperty3::GetCustomViewerCount
helpviewer_keywords:
- IDebugProperty3::GetCustomViewerCount
ms.assetid: dc5bb3e4-dc85-46e4-98fa-c6be8583b985
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: af4a1ee246c2e04256ad5cb5b40644084e8c34ae
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47570123"
---
# <a name="idebugproperty3getcustomviewercount"></a>IDebugProperty3::GetCustomViewerCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugProperty3::GetCustomViewerCount](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugproperty3-getcustomviewercount).  
  
Возвращает количество пользовательских средств просмотра, которые могут быть доступны для этого свойства.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetCustomViewerCount(  
   ULONG* pcelt  
);  
```  
  
```csharp  
int GetCustomViewerCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pcelt`  
 [out] Число пользовательских средств просмотра, доступные для этого свойства.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Чтобы обеспечить поддержку визуализаторов типов, этот метод перенаправляет вызов [GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md) метод. Если средство оценки выражений также поддерживает пользовательские средства просмотра для этого свойства типа, этот метод добавляет число пользовательских средств просмотра, к возвращенному значению.  
  
 Подробные сведения о различиях между визуализаторов типов и пользовательских средств просмотра, см. в разделе [визуализатор типов и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md).  
  
## <a name="example"></a>Пример  
 В следующем примере показано, как реализовать этот метод для **CProperty** объекта, который предоставляет [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) интерфейс.  
  
```cpp#  
STDMETHODIMP CProperty::GetCustomViewerCount(ULONG* pcelt)  
{  
    if (pcelt == NULL)  
    {  
        return E_POINTER;  
    }  
  
    if (GetVisualizerService())  
    {  
        return m_pIEEVisualizerService->GetCustomViewerCount(pcelt);  
    }  
    else  
    {  
        return E_NOTIMPL;  
    }  
}  
```  
  
## <a name="see-also"></a>См. также  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [GetCustomViewerCount](../../../extensibility/debugger/reference/ieevisualizerservice-getcustomviewercount.md)   
 [Визуализатор типов и пользовательское средство просмотра](../../../extensibility/debugger/type-visualizer-and-custom-viewer.md)


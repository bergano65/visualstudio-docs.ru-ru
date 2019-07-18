---
title: IEEVisualizerServiceProvider::CreateVisualizerService | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ed8327690c42f54a33209b2f0acfa45a138ec51c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68155081"
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод создает службу визуализатора.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT CreateVisualizerService(  
   IDebugBinder*              binder,  
   IDebugSymbolProvider*      pSymProv,  
   IDebugAddress*             pAddress,  
   IEEVisualizerDataProvider* dataProvider,  
   IEEVisualizerService**     ppService  
);  
```  
  
```csharp  
int CreateVisualizerService(  
   IDebugBinder binder,  
   IDebugSymbolProvider      pSymProv,  
   IDebugAddress             pAddress,  
   IEEVisualizerDataProvider dataProvider,  
   out IEEVisualizerService  ppService  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `binder`  
 [in] [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) объект, передаваемый в [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md).  
  
 `pSymProv`  
 [in] [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) объект, передаваемый в `IDebugParsedExpression::EvaluateSync`.  
  
 `pAddress`  
 [in] [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) объект, передаваемый в `IDebugParsedExression::EvaluateSync`.  
  
 `dataProvider`  
 [in] Объект, реализующий интерфейс [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) интерфейс (указанного в вычислителе выражений).  
  
 `ppService`  
 [out] Служба создана.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 `binder`, `pSymProv`, И `pAddress` параметры были переданы для `IDebugParsedExpression::EvaluateSync` метод. `CreateVisualizerService` должна быть вызвана только из `IDebugParsedExpression::EvaluateSync` как часть вычислитель выражений поддержка визуализаторами типов.  
  
## <a name="see-also"></a>См. также  
 [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)   
 [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)   
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

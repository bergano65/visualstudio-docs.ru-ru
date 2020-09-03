---
title: 'Иивисуализердатапровидер:: Жетобжектфорвисуализер | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::GetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::GetObjectForVisualizer method
ms.assetid: bd5376fc-13b4-40b7-9a5d-7ba8289f1b24
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 88562ae2238f33f1f46913a42df44fcb482cc8fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192071"
---
# <a name="ieevisualizerdataprovidergetobjectforvisualizer"></a>IEEVisualizerDataProvider::GetObjectForVisualizer
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод получает объект, представляемый этим визуализатором.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetObjectForVisualizer(  
   IDebugObject** ppObject  
);  
```  
  
```csharp  
int GetObjectForVisualizer(  
   out IDebugObject ppObject  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppObject`  
 заполняет Объект, представляемый этим визуализатором  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 `GetObjectForVisualizer` может возвращать кэшированную версию объекта. Если вызывающий объект хочет обеспечить актуальность объекта, он будет вызывать [жетневобжектфорвисуализер](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md).  
  
## <a name="see-also"></a>См. также:  
 [иивисуализердатапровидер](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [жетневобжектфорвисуализер](../../../extensibility/debugger/reference/ieevisualizerdataprovider-getnewobjectforvisualizer.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)

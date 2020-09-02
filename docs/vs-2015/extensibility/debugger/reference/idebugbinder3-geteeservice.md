---
title: 'IDebugBinder3:: Жетисервице | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetEEService
helpviewer_keywords:
- IDebugBinder3::GetEEService method
ms.assetid: eb07aa40-8cd9-4a52-a4c7-4affd2307a01
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 982802d1e89434322aba4f5078ceb6dd5a850034
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193044"
---
# <a name="idebugbinder3geteeservice"></a>IDebugBinder3::GetEEService
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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
 [входные] `GUID` поставщика (значение NULL приемлемо).  
  
 `language`  
 [входные] `GUID` языка (значение NULL допустимо).  
  
 `iid`  
 [входные] `IID` получаемой службы.  
  
 `ppService`  
 заполняет Интерфейс для запрошенной службы.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Передайте значение `IID` для интерфейса [иивисуализерсервицепровидер](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md) ( `IID_IEEVisualizerServiceProvider` ), чтобы узнать, доступна ли служба визуализатора типов. Если это так, средство оценки выражений может получить интерфейс [иивисуализерсервице](../../../extensibility/debugger/reference/ieevisualizerservice.md) для поддержки визуализаторов типов. Дополнительные сведения см. в разделе [визуализация и просмотр данных](../../../extensibility/debugger/visualizing-and-viewing-data.md) .  
  
## <a name="see-also"></a>См. также:  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [иивисуализерсервицепровидер](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)   
 [иивисуализерсервице](../../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [Визуализация и просмотр данных](../../../extensibility/debugger/visualizing-and-viewing-data.md)

---
title: IEEVisualizerService::GetValueDisplayStringCount | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IEEVisualizerService::GetValueDisplayStringCount
- GetValueDisplayStringCount
ms.assetid: d683a833-fbfb-4042-84df-6905124a268a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8af1b785e56d5efba2505b0cdbd5a9474b5c261b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53957953"
---
# <a name="ieevisualizerservicegetvaluedisplaystringcount"></a>IEEVisualizerService::GetValueDisplayStringCount
Возвращает номер строки значение указанного свойства или поля.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetValueDisplayStringCount (  
   DWORD         displayKind,   
   IDebugField * propertyOrField,   
   ULONG *       pcelt  
);  
```  
  
```csharp  
int GetValueDisplayStringCount (  
   uint        displayKind,   
   IDebugField propertyOrField,   
   out ulong   pcelt  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `displayKind`  
 [in] Значение из [DisplayKind](../../../extensibility/debugger/reference/displaykind.md) перечисления.  
  
 `propertyOrField`  
 [in] [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) интерфейс, который представляет свойство или поле.  
  
 `pcelt`  
 [out] Возвращает число строк, значение для отображения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IEEVisualizerService](../../../extensibility/debugger/reference/ieevisualizerservice.md)
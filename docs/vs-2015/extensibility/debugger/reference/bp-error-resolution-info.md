---
title: BP_ERROR_RESOLUTION_INFO | Документация Майкрософт
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
- BP_ERROR_RESOLUTION_INFO
helpviewer_keywords:
- BP_ERROR_RESOLUTION_INFO structure
ms.assetid: a6b83242-5728-4716-80f3-840c96d59c6c
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b70490cebb2e2ac62268d4419e1484f3ecfa4029
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745303"
---
# <a name="bperrorresolutioninfo"></a>BP_ERROR_RESOLUTION_INFO
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Описание разрешения ошибки точки останова, включая расположение, программы и потока.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
typedef struct _BP_ERROR_RESOLUTION_INFO {   
   BPERESI_FIELDS         dwFields;  
   BP_RESOLUTION_LOCATION bpResLocation;  
   IDebugProgram2*        pProgram;  
   IDebugThread2*         pThread;  
   BSTR                   bstrMessage;  
   BP_ERROR_TYPE          dwType;  
} BP_ERROR_RESOLUTION_INFO;  
```  
  
```csharp  
public struct BP_ERROR_RESOLUTION_INFO {   
   public uint                   dwFields;  
   public BP_RESOLUTION_LOCATION bpResLocation;  
   public IDebugProgram2         pProgram;  
   public IDebugThread2          pThread;  
   public string                 bstrMessage;  
   public uint                   dwType;  
};  
```  
  
## <a name="members"></a>Участники  
 `dwFields`  
 Сочетание значений из [BPERESI_FIELDS](../../../extensibility/debugger/reference/bperesi-fields.md) перечисление, определяющее, вы заполните все поля этой структуры.  
  
 `bpResLocation`  
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) union, указывающий положение точки останова разрешения.  
  
 `pProgram`  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) объект, представляющий приложение, в котором произошла ошибка точки останова.  
  
 `pThread`  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , представляющий поток, на котором выполняется приложение, вызвавшего ошибку точки останова.  
  
 `bstrMessage`  
 Строка, содержащая предупреждения или ошибки сообщения, полученные в результате Устранение этой ошибки.  
  
 `dwType`  
 Значение из [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md) перечисление, указывающее тип ошибки точки останова.  
  
## <a name="remarks"></a>Примечания  
 Эта структура возвращается из [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetResolutionInfo](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2-getresolutioninfo.md)   
 [BPRESI_FIELDS](../../../extensibility/debugger/reference/bpresi-fields.md)   
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP_ERROR_TYPE](../../../extensibility/debugger/reference/bp-error-type.md)


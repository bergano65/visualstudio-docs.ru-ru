---
title: "IDebugCanStopEvent2::GetReason | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: b5d4c50b407406ea9a5d878decf859b8ab70863d
ms.contentlocale: ru-ru
ms.lasthandoff: 09/06/2017

---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
Возвращает причину, почему хочет остановить отладчик (DE).  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetReason(   
   CANSTOP_REASON* pcr  
);  
```  
  
```csharp  
int GetReason(   
   out enum_CANSTOP_REASON pcr  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pcr`  
 [out] Возвращает значение из [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) перечисления, которое описывает причину возникновения данного события.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод обычно вызывается перед [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) метод, чтобы вызывающий объект мог определить, следует ли передавать ненулевое значение (`TRUE`) для `IDebugCanStopEvent2::CanStop` метод.  
  
 Причина остановки может быть как `CANSTOP_ENTRYPOINT`, означающее DE достиг точки входа или `CANSTOP_STEPIN`, означающее DE шаг с заходом в функцию.  
  
## <a name="see-also"></a>См. также  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)   
 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)

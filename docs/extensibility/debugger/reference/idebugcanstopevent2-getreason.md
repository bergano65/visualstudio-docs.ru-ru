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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: d6b75ff3e3fc74018bb8f17d7754183309ea39c3
ms.lasthandoff: 02/22/2017

---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
Возвращает причину, почему отладчик (DE) должно быть остановлено.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetReason(   
   CANSTOP_REASON* pcr  
);  
```  
  
```c#  
int GetReason(   
   out enum_CANSTOP_REASON pcr  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pcr`  
 [out] Возвращает значение из [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) перечисление, описывающее причину данного события.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Обычно этот метод вызывается перед [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) метод, вызывающий объект определяет, следует ли передавать ненулевое значение (`TRUE`) для `IDebugCanStopEvent2::CanStop` метод.  
  
 Причина остановки может быть либо `CANSTOP_ENTRYPOINT`, означающее DE достиг точки входа или `CANSTOP_STEPIN`, означающее DE зашел в функцию.  
  
## <a name="see-also"></a>См. также  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)   
 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)

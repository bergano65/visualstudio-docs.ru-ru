---
title: 'IDebugCanStopEvent2:: Reason | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 707488abed004adaa75c84f16358bdd8a979eb71
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68191152"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает причину, по которой подсистема отладки (DE) должна быть приостановлена.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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
 заполняет Возвращает значение из перечисления [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) , которое описывает причину для этого события.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Возвращает значение `S_OK`, если выполнение прошло успешно; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Этот метод обычно вызывается перед методом [канстоп](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) , чтобы вызывающий объект мог определить, передавать ли метод ненулевое значение ( `TRUE` ) `IDebugCanStopEvent2::CanStop` .  
  
 Причиной для остановки может быть либо, что означает, что `CANSTOP_ENTRYPOINT` de достиг точки входа, либо, что означает, что `CANSTOP_STEPIN` функция de пошагова в функцию.  
  
## <a name="see-also"></a>См. также:  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)   
 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)

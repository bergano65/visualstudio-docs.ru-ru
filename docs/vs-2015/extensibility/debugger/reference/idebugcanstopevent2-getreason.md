---
title: IDebugCanStopEvent2::GetReason | Документация Майкрософт
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
- IDebugCanStopEvent2::GetReason
helpviewer_keywords:
- IDebugCanStopEvent2::GetReason
ms.assetid: f5de31ca-7b8d-4029-9cf9-ba860ac66af6
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fcc130a2b6dc1874c1ac536ae2e7d13aa3db4952
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568283"
---
# <a name="idebugcanstopevent2getreason"></a>IDebugCanStopEvent2::GetReason
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugCanStopEvent2::GetReason](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcanstopevent2-getreason).  
  
Возвращает причину, почему хочет остановить отладчик (DE).  
  
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
 [out] Возвращает значение из [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md) перечисление, описывающее причину для данного события.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Этот метод обычно вызывается перед [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md) метод, чтобы вызывающий объект мог определить, нужно ли передать ненулевое значение (`TRUE`) для `IDebugCanStopEvent2::CanStop` метод.  
  
 Причина остановки может быть либо `CANSTOP_ENTRYPOINT`, означающее DE достиг точки входа или `CANSTOP_STEPIN`, означающее DE шаг с заходом в функцию.  
  
## <a name="see-also"></a>См. также  
 [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md)   
 [CANSTOP_REASON](../../../extensibility/debugger/reference/canstop-reason.md)   
 [CanStop](../../../extensibility/debugger/reference/idebugcanstopevent2-canstop.md)


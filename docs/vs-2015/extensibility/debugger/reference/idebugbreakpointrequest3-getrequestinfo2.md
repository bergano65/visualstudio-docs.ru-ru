---
title: IDebugBreakpointRequest3::GetRequestInfo2 | Документация Майкрософт
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
- IDebugBreakpointRequest3::GetRequestInfo2
helpviewer_keywords:
- IDebugBreakpointRequest3::GetRequestInfo2
ms.assetid: 33942e4a-0a0a-49e8-a693-004954f6d38a
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 62c04aef42571eebe96e2f03b3cc99eedd8e7b3e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47573374"
---
# <a name="idebugbreakpointrequest3getrequestinfo2"></a>IDebugBreakpointRequest3::GetRequestInfo2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [IDebugBreakpointRequest3::GetRequestInfo2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2).  
  
Этот метод получает данные запроса точки останова, описывающие этот запрос точки останова.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetRequestInfo2(  
   BPREQI_FIELDS      dwFields,  
   BP_REQUEST_INFO2*  bBPRequestInfo  
);  
```  
  
```csharp  
int GetRequestInfo2(  
   enum_BPREQI_FIELDS  dwFields,   
   BP_REQUEST_INFO2[]  bBPRequestInfo  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwFields`  
 [in] Сочетание флагов из [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) перечисление, определите, какие поля из `pBPRequestInfo` должны быть заполнены.  
  
 `bBPRequestInfo`  
 [out] [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) структуры для заполнения.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Дополнительные сведения в этом запросе, не возвращаются из [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md) метод.  
  
## <a name="see-also"></a>См. также  
 [IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)   
 [GetRequestInfo](../../../extensibility/debugger/reference/idebugbreakpointrequest2-getrequestinfo.md)   
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)   
 [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)


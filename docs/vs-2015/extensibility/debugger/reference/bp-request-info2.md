---
title: BP_REQUEST_INFO2 | Документация Майкрософт
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
- BP_REQUEST_INFO2
helpviewer_keywords:
- BP_REQUEST_INFO2 structure
ms.assetid: 008c87f7-a76e-43d3-8904-11b225d6a9a5
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5568e696f8463e2a8e5c64467bc82f192d790b5e
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558356"
---
# <a name="bprequestinfo2"></a>BP_REQUEST_INFO2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [BP_REQUEST_INFO2](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/bp-request-info2).  
  
Содержит сведения, необходимые для реализации точки останова, включая идентификатор GUID поставщика, ограничения и трассировки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
typedef struct _BP_REQUEST_INFO2 {  
   BPREQI_FIELDS   dwFields;  
   GUID            guidLanguage;  
   BP_LOCATION     bpLocation;  
   IDebugProgram2* pProgram;  
   BSTR            bstrProgramName;  
   IDebugThread2*  pThread;  
   BSTR            bstrThreadName;  
   BP_CONDITION    bpCondition;  
   BP_PASSCOUNT    bpPassCount;  
   BP_FLAGS        dwFlags;  
   GUID            guidVendor;  
   BSTR            bstrConstraint;  
   BSTR            bstrTracepoint;  
} BP_REQUEST_INFO2;  
```  
  
```csharp  
public struct BP_REQUEST_INFO2 {  
   public uint           dwFields;  
   public Guid           guidLanguage;  
   public BP_LOCATION    bpLocation;  
   public IDebugProgram2 pProgram;  
   public string         bstrProgramName;  
   public IDebugThread2  pThread;  
   public string         bstrThreadName;  
   public BP_CONDITION   bpCondition;  
   public BP_PASSCOUNT   bpPassCount;  
   public uint           dwFlags;  
   public Guid           guidVendor;  
   public string         bstrConstraint;  
   public string         bstrTracepoint;  
};  
```  
  
## <a name="members"></a>Участники  
 `dwFields`  
 Сочетание флагов из [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md) перечисление, указывающее, какие поля заполнены.  
  
 `guidLanguage`  
 GUID языка.  
  
 `bpLocation`  
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) структуру, которая указывает тип точки останова.  
  
 `pProgram`  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) объект, представляющий приложение, в котором происходит точки останова.  
  
 `bstrProgramName`  
 Имя приложения, в котором происходит точки останова.  
  
 `pThread`  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) , представляющий поток, в котором происходит точки останова.  
  
 `bstrThreadName`  
 Имя потока, в котором происходит точки останова.  
  
 `bpCondition`  
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) структуру, которая описывает условия, при которых точка останова будет срабатывать.  
  
 `bpPassCount`  
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) структуру, содержащую сведения о подсчете pass точки останова.  
  
 `dwFlags`  
 Сочетание флагов из [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md) перечисления, указывающее флаги для запрошенного точки останова.  
  
 `guidVendor`  
 Идентификатор GUID поставщика. Может иметь значение null.  
  
 `bstrConstraint`  
 Имя ограничения точки останова. Может иметь значение null.  
  
 `bstrTracepoint`  
 Имя точки трассировки. Может иметь значение null.  
  
## <a name="remarks"></a>Примечания  
 Эта структура возвращается [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md) метод.  
  
## <a name="requirements"></a>Требования  
 Заголовок: msdbg.h  
  
 Пространство имен: Microsoft.VisualStudio.Debugger.Interop  
  
 Сборка: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>См. также  
 [Структуры и объединения](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetRequestInfo2](../../../extensibility/debugger/reference/idebugbreakpointrequest3-getrequestinfo2.md)   
 [BPREQI_FIELDS](../../../extensibility/debugger/reference/bpreqi-fields.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)   
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)   
 [BP_FLAGS](../../../extensibility/debugger/reference/bp-flags.md)


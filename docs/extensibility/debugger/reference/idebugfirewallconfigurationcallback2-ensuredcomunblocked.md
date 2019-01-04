---
title: IDebugFirewallConfigurationCallback2::EnsureDCOMUnblocked | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- EnsureDCOMUnblocked
- IDebugFirewallConfigurationCallback2::EnsureDCOMUnblocked
ms.assetid: acf54d27-32a6-47e7-aba6-3cc0004edc7f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f7a916395ab6fa83c8da30cdc6fb5b510069cbe3
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53887296"
---
# <a name="idebugfirewallconfigurationcallback2ensuredcomunblocked"></a>IDebugFirewallConfigurationCallback2::EnsureDCOMUnblocked
Запросы, что брандмауэр не блокирует удаленную отладку.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT EnsureDCOMUnblocked(   
    Void  
);  
```  
  
```csharp  
public int EnsureDCOMUnblocked();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md)
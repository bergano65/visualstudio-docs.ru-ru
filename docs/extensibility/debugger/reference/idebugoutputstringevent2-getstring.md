---
title: IDebugOutputStringEvent2::GetString | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugOutputStringEvent2::GetString
helpviewer_keywords:
- IDebugOutputStringEvent2::GetString
ms.assetid: f059f8e0-ad44-49ac-ba90-73576ada5e06
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1930c20f1ffd44b0dfa574b46753d96139caf110
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53985554"
---
# <a name="idebugoutputstringevent2getstring"></a>IDebugOutputStringEvent2::GetString
Получает отображаемое сообщение.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetString(   
   BSTR* pbstrString  
);  
```  
  
```csharp  
int GetString(   
   out string pbstrString  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pbstrString`  
 [out] Возвращает отображаемое сообщение.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md)
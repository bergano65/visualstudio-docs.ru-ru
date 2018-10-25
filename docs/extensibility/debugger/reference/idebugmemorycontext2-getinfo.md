---
title: IDebugMemoryContext2::GetInfo | Документация Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMemoryContext2::GetInfo
helpviewer_keywords:
- GetInfo method
- IDebugMemoryContext2::GetInfo method
ms.assetid: 08c7f091-1816-4d64-8834-f9ecaac5c58d
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 2c76d197a03d644fa841e55e7e7910f4d0541840
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49841992"
---
# <a name="idebugmemorycontext2getinfo"></a>IDebugMemoryContext2::GetInfo
Извлекает [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) структура, описывающая контекст.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetInfo(   
   CONTEXT_INFO_FIELDS dwFields,  
   CONTEXT_INFO*       pInfo  
);  
```  
  
```csharp  
int GetInfo(  
   enum_CONTEXT_INFO_FIELDS dwFields,   
   CONTEXT_INFO[]           pinfo  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `dwFields`  
 [in] Сочетание флагов из [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) перечисления, которые указывают, какие поля [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) структуры, должны заполнить.  
  
 `pInfo`  
 [in, out] `CONTEXT_INFO` Структура, которая заполняется.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)   
 [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)   
 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)
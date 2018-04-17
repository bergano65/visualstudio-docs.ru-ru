---
title: IDebugExpressionEvaluator2::GetService | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: cfde812730a5f9d2fbad3144cf4298472ec2f8c5
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="idebugexpressionevaluator2getservice"></a>IDebugExpressionEvaluator2::GetService
Получает объект службы по заданному идентификатору.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetService (  
   GUID        uid,  
   IUnknown ** ppService  
);  
```  
  
```csharp  
int GetService (  
   Guid       uid,  
   out object ppService  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `uid`  
 [in] Уникальный идентификатор службы для извлечения.  
  
 `ppService`  
 [out] Возвращает объект, представляющий службу.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Это может использоваться независимых выражений для получения служб от другого средство оценки выражений. Например этот метод может использоваться для получения интерфейса службы визуализатора из выражений по умолчанию. Вычислители выражений сторонних скорее всего потребуются для реализации этого интерфейса.  
  
## <a name="see-also"></a>См. также  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
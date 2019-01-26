---
title: IDebugExpressionEvaluator2::GetService | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1ff1db8b4e8b842a9c2ec19ff2a454ce55cf7992
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54976158"
---
# <a name="idebugexpressionevaluator2getservice"></a>IDebugExpressionEvaluator2::GetService
Извлекает объект службы по заданному идентификатору.  
  
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
 [in] Уникальный идентификатор извлекаемой службы.  
  
 `ppService`  
 [out] Возвращает объект, представляющий службу.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Это может быть поглощен вычислитель выражений независимых производителей для получения служб из другой средство оценки выражений. Например этот метод может использоваться для получения интерфейса для службы визуализатора из средство оценки выражений по умолчанию. Вычислители выражений сторонних вряд ли должны реализовать этот интерфейс.  
  
## <a name="see-also"></a>См. также  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
---
title: IDebugExpressionEvaluator2::GetService | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::GetService
- GetService
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: af73b23cfaf0b282403e8e6a94d6f05db419bd41
ms.sourcegitcommit: da4079f5b6ec884baf3108cbd0519d20cb64c70b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2019
ms.locfileid: "62540346"
---
# <a name="idebugexpressionevaluator2getservice"></a>IDebugExpressionEvaluator2::GetService
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Извлекает объект службы по заданному идентификатору.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
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

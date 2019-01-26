---
title: IDebugEvent2::GetAttributes | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugEvent2::GetAttributes
helpviewer_keywords:
- IDebugEvent2::GetAttributes
ms.assetid: 2ac5b5fb-da17-43f7-811a-313f677e60d7
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dffc2bbd858fa7c8bcc31825de79dcdc4b9a60ac
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "55040194"
---
# <a name="idebugevent2getattributes"></a>IDebugEvent2::GetAttributes
Получает атрибуты для этого события отладки.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetAttribute(   
   DWORD* pdwAttrib  
);  
```  
  
```csharp  
int GetAttribute(   
   out uint pdwAttrib  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pdwAttrib`  
 [out] Сочетание флагов из [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md) перечисления.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) интерфейса являются общими для всех событий. Этот метод описывается тип события; Например такое событие синхронным или асинхронным и она событии остановки.  
  
## <a name="see-also"></a>См. также  
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [EVENTATTRIBUTES](../../../extensibility/debugger/reference/eventattributes.md)
---
title: IDebugObject2::IsEncOutdated | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugObject2::IsEncOutdated
helpviewer_keywords:
- IDebugObject2::IsEncOutdated method
ms.assetid: d3a8c02d-895b-478c-9957-d663130f308e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a7f8344896c0ad262a8db09cb4caa0e00414431b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53838889"
---
# <a name="idebugobject2isencoutdated"></a>IDebugObject2::IsEncOutdated
Этот метод определяет, является ли устаревших изменить и продолжить состояние этого объекта или родительского контейнера. Вычислитель пользовательское выражение не реализует этот метод и всегда возвращает `E_NOTIMPL`.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT IsEncOutdated(  
   BOOL* pfEncOutdated  
);  
```  
  
```csharp  
int IsEncOutdated(  
   out int pfEncOutdated  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pfEncOutdated`  
 [out] Ненулевое значение (`TRUE`), если изменить и продолжить состояние устаревшей, ноль (`FALSE`) Если это не так.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
> [!NOTE]
>  Вычислитель пользовательское выражение всегда должны возвращать `E_NOTIMPL`.  
  
## <a name="see-also"></a>См. также  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
---
title: IDebugField::Equal | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0157a09390bd6e8380e97cef8e4c4158c75ac3ab
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53918827"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
Этот метод сравнивает это поле с указанным полем на предмет равенства.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Equal(   
   IDebugField* pField  
);  
```  
  
```csharp  
int Equal(  
   IDebugField pField  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pField`  
 [in] Поле для сравнения с этим параметром.  
  
## <a name="return-value"></a>Возвращаемое значение  
 Если поля не изменилось, возвращает `S_OK`. Если поля не совпадают, возвращает `S_FALSE.` в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
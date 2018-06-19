---
title: IDebugExtendedField::IsClosedType | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IsClosedType
- IDebugExtendedField::IsClosedType
ms.assetid: 9136fc57-74ff-4fe4-a6e2-b137cb9d5b08
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 00c1e8bc4eba53a3109f08dc1b8d17c2901612c4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31122500"
---
# <a name="idebugextendedfieldisclosedtype"></a>IDebugExtendedField::IsClosedType
Определяет, представляет ли поле закрытого типа.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT IsClosedType(  
   void  
);  
```  
  
```csharp  
int IsClosedType();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Если поле является закрытым типом, возвращает `S_OK`; в противном случае возвращает `S_FALSE`.  
  
## <a name="see-also"></a>См. также  
 [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)
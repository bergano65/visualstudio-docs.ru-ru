---
title: 'Идебужекстендедфиелд:: Исклоседтипе | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IsClosedType
- IDebugExtendedField::IsClosedType
ms.assetid: 9136fc57-74ff-4fe4-a6e2-b137cb9d5b08
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a1cf28e8391a1dd37949c042bd7d58d9c8b7da06
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148981"
---
# <a name="idebugextendedfieldisclosedtype"></a>IDebugExtendedField::IsClosedType
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Определяет, представляет ли поле закрытый тип.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT IsClosedType(  
   void  
);  
```  
  
```csharp  
int IsClosedType();  
```  
  
## <a name="return-value"></a>Возвращаемое значение  
 Если поле является закрытым типом, возвращает `S_OK` ; в противном случае возвращает `S_FALSE` .  
  
## <a name="see-also"></a>См. также:  
 [IDebugExtendedField](../../../extensibility/debugger/reference/idebugextendedfield.md)

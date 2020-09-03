---
title: 'Иенумдебугобжектс:: Skip | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugObjects::Skip
helpviewer_keywords:
- IEnumDebugObjects::Skip method
ms.assetid: 957cead8-0a9c-4403-b190-b9fbadc49d42
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b6333c9474ea2bb40f4327d2ebdd7595722cf1b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180466"
---
# <a name="ienumdebugobjectsskip"></a>IEnumDebugObjects::Skip
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод пропускает указанное число элементов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Skip(  
   [in] ULONG celt  
);  
```  
  
```csharp  
int Skip(  
   [In] uint celt  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `celt`  
 [in] Число пропускаемых элементов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` `celt` , если больше числа оставшихся элементов; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Если `celt` задает значение, превышающее число оставшихся элементов, перечисление устанавливается в конец и `S_FALSE` возвращается.  
  
## <a name="see-also"></a>См. также:  
 [IEnumDebugObjects](../../../extensibility/debugger/reference/ienumdebugobjects.md)

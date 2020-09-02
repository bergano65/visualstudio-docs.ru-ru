---
title: 'Иенумдебугфиелдс:: Next | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugFields::Next
helpviewer_keywords:
- IEnumDebugFields::Next method
ms.assetid: 22c177a2-af81-4234-812b-f9b47be245a2
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7a6cdf99bdfce0b53bf431bf456c276bb88b87e4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199643"
---
# <a name="ienumdebugfieldsnext"></a>IEnumDebugFields::Next
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Этот метод возвращает следующий набор элементов из перечисления.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Next(  
   ULONG         celt,  
   IDebugField** rgelt,  
   ULONG*        pceltFetched  
);  
```  
  
```csharp  
int Next(  
   uint          celt,  
   IDebugField[] rgelt,  
   ref uint      pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `celt`  
 [in] Количество получаемых элементов. Также указывает максимальный размер `rgelt` массива.  
  
 `rgelt`  
 [вход, выход] Массив элементов [идебугфиелд](../../../extensibility/debugger/reference/idebugfield.md) , которые должны быть заполнены.  
  
 `pceltFetched`  
 заполняет Возвращает количество элементов, фактически возвращаемых в `rgelt` .  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает `S_OK`. Возвращает `S_FALSE` , если может быть возвращено меньше запрошенного числа элементов; в противном случае возвращает код ошибки.  
  
## <a name="see-also"></a>См. также:  
 [иенумдебугфиелдс](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

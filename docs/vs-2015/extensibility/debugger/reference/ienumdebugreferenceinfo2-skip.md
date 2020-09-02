---
title: 'IEnumDebugReferenceInfo2:: Skip | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugReferenceInfo2::Skip
helpviewer_keywords:
- IEnumDebugReferenceInfo2::Skip
ms.assetid: 12f07ed8-92bd-47b5-9113-f73fec5bdde6
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 03cda5d1134032c5d2e5f4bcdad8af1d5e647758
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68147757"
---
# <a name="ienumdebugreferenceinfo2skip"></a>IEnumDebugReferenceInfo2::Skip
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Пропускает заданное число элементов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
```csharp  
int Skip(  
   uint celt  
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
 [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)

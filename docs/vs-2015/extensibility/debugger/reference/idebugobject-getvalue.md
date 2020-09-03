---
title: 'Идебугобжект:: GetValue | Документация Майкрософт'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject::GetValue
helpviewer_keywords:
- IDebugObject::GetValue method
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: de6e6888cfce338ebcee90e722f07e900ce25d0b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180534"
---
# <a name="idebugobjectgetvalue"></a>IDebugObject::GetValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Возвращает значение объекта в виде последовательности байтов.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp#  
HRESULT GetValue(   
   BYTE* pValue,  
   UINT  nSize  
);  
```  
  
```csharp  
int GetValue(  
   ref byte[] pValue,   
   uint nSize  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `pValue`  
 [вход, выход] Массив, который заполняется последовательными последовательностями байтов, представляющими значение объекта.  
  
 `nSize`  
 окне Максимальное число извлекаемых байтов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успеха возвращает S_OK; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Remarks  
 Возвращает общее количество байтов значений, которые можно получить, вызвав [метод GetBytes](../../../extensibility/debugger/reference/idebugobject-getsize.md) .  
  
## <a name="see-also"></a>См. также:  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)

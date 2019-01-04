---
title: IEnumDebugFields::Reset | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IEnumDebugFields::Reset
helpviewer_keywords:
- IEnumDebugFields::Reset method
ms.assetid: 38ff61e4-0120-42e8-971a-16be6050b425
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8f1de86cda120d33db201907dca55c07a1c75782
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53839155"
---
# <a name="ienumdebugfieldsreset"></a>IEnumDebugFields::Reset
Этот метод выполняет сброс перечисления к первому элементу.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT Reset(void);  
```  
  
```csharp  
int Reset();  
```  
  
#### <a name="parameters"></a>Параметры  
 Нет  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## <a name="remarks"></a>Примечания  
 После вызова этого метода, следующий вызов [Далее](../../../extensibility/debugger/reference/ienumdebugfields-next.md) возвращает первый элемент перечисления.  
  
## <a name="see-also"></a>См. также  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [Вперед](../../../extensibility/debugger/reference/ienumdebugfields-next.md)
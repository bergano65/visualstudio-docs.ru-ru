---
title: IDebugClassField::EnumNestedClasses | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugClassField::EnumNestedClasses
helpviewer_keywords:
- IDebugClassField::EnumNestedClasses method
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1db2786de20bdb845fb40ed37d4d97f49b718b3c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53908505"
---
# <a name="idebugclassfieldenumnestedclasses"></a>IDebugClassField::EnumNestedClasses
Создает перечислитель для классов, вложенные в этот класс.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT EnumNestedClasses(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumNestedClasses(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppEnum`  
 [out] Возвращает [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) объект, представляющий список вложенных классов. Возвращает значение null, если нет вложенных классов.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK, или возвращает S_FALSE, если нет вложенных классов. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Каждый элемент перечисления является [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) описывающий вложенного класса.  
  
 Вложенный класс — это класс, определенный внутри другого класса. Пример:  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) перечисления будет содержать один объект, представляющий `NestedClass` класса.  
  
## <a name="see-also"></a>См. также  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
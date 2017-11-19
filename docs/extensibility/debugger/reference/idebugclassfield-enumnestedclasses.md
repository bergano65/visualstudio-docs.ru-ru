---
title: "IDebugClassField::EnumNestedClasses | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugClassField::EnumNestedClasses
helpviewer_keywords: IDebugClassField::EnumNestedClasses method
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 51b8c582d221ced72380cf5450fc0af9b014d148
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
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
 В случае успешного выполнения возвращает значение S_OK, или возвращает значение S_FALSE, если нет вложенных классов. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Каждый элемент перечисления является [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) объект, описывающий вложенный класс.  
  
 Вложенный класс — это класс, определенный внутри другого класса. Пример:  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) перечисления должен содержать один объект, представляющий `NestedClass` класса.  
  
## <a name="see-also"></a>См. также  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
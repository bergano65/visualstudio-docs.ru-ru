---
title: IDebugClassField::EnumConstructors | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugClassField::EnumConstructors
helpviewer_keywords:
- IDebugClassField::EnumConstructors method
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: c73650ceb0282d356b0b473adab4d33869d58360
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53950885"
---
# <a name="idebugclassfieldenumconstructors"></a>IDebugClassField::EnumConstructors
Создает перечислитель для конструкторов для данного класса.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT EnumConstructors(   
   CONSTRUCTOR_ENUM   cMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumConstructors(  
   CONSTRUCTOR_ENUM     cMatch,   
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `cMatch`  
 [in] Значение из [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) перечисления, указывающее тип конструкторов для перечисления.  
  
 `ppEnum`  
 [out] Возвращает [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) объект, представляющий список конструкторов. Возвращает значение null, если конструкторы отсутствуют.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK, или возвращает S_FALSE, если конструкторы отсутствуют. В противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Каждый элемент перечисления является [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) объект, описывающий метод-конструктор.  
  
 Список конструкторов обычно не включает конструкторы по умолчанию, предоставленные с помощью компилятора.  
  
## <a name="see-also"></a>См. также  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [CONSTRUCTOR_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)
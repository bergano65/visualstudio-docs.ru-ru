---
title: IDebugClassField::GetEnclosingClass | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugClassField::GetEnclosingClass
helpviewer_keywords:
- IDebugClassField::GetEnclosingClass method
ms.assetid: a0c12e3c-9ea0-4dfb-9e45-8cea18725022
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6cd73955835f8aff0047995a690da03e5ab0305d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31105831"
---
# <a name="idebugclassfieldgetenclosingclass"></a>IDebugClassField::GetEnclosingClass
Возвращает класс, который содержит этот класс.  
  
## <a name="syntax"></a>Синтаксис  
  
```cpp  
HRESULT GetEnclosingClass(   
   IDebugClassField** ppClassField  
);  
```  
  
```csharp  
int GetEnclosingClass(  
   out IDebugClassField ppClassField  
);  
```  
  
#### <a name="parameters"></a>Параметры  
 `ppClassField`  
 [out] Возвращает [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) объект, представляющий включающий класс. Возвращает значение null, если нет включающего класса.  
  
## <a name="return-value"></a>Возвращаемое значение  
 В случае успешного выполнения возвращает значение S_OK; в противном случае возвращается код ошибки.  
  
## <a name="remarks"></a>Примечания  
 Если класс представленный этим [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) объекта является вложенным классом, а затем `ppClassField` параметр возвращает `IDebugClassField` объект, представляющий включающий класс. Например рассмотрим следующее определение класса:  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 Вызов `GetEnclosingClass` метод `IDebugClassField` , представляющий `NestedClass` возвращает `IDebugClassField` объект, представляющий класс `RootClass`.  
  
## <a name="see-also"></a>См. также  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
---
title: "IDebugClassField::EnumNestedClasses | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugClassField::EnumNestedClasses"
helpviewer_keywords: 
  - "Метод IDebugClassField::EnumNestedClasses"
ms.assetid: 2ba5ef0c-395e-4006-9e3c-9b06e1d711d0
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugClassField::EnumNestedClasses
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Создает перечислитель для классов, вложенные в этом классе.  
  
## Синтаксис  
  
```cpp#  
HRESULT EnumNestedClasses(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int EnumNestedClasses(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### Параметры  
 `ppEnum`  
 \[out\] возвращает [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) объект, представляющий список вложенных классов.  Возвращает значение NULL, если вложенные классы.  
  
## Возвращаемое значение  
 В случае успеха возвращает значение S\_OK и возвращает значение S\_FALSE, если вложенные классы.  В противном случае возвращает код ошибки.  
  
## Заметки  
 Каждый элемент перечисления [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) объект, описывающий вложенный класс.  
  
 Вложенный класс класс, определенный внутри другого класса.  Примеры.  
  
```  
class RootClass {  
   class NestedClass { }  
};  
```  
  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) перечисление содержал бы один представления объекта  `NestedClass` класс.  
  
## См. также  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
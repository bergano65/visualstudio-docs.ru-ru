---
title: "IDebugClassField::EnumConstructors | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugClassField::EnumConstructors"
helpviewer_keywords: 
  - "Метод IDebugClassField::EnumConstructors"
ms.assetid: 66a250b2-75a0-45aa-8d58-40f91cc4bf7b
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugClassField::EnumConstructors
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Создает перечислитель для конструкторов для этого класса.  
  
## Синтаксис  
  
```cpp#  
HRESULT EnumConstructors(   
   CONSTRUCTOR_ENUM   cMatch,  
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int EnumConstructors(  
   CONSTRUCTOR_ENUM     cMatch,   
   out IEnumDebugFields ppEnum  
);  
```  
  
#### Параметры  
 `cMatch`  
 \[in\] значение из [CONSTRUCTOR\_ENUM](../../../extensibility/debugger/reference/constructor-enum.md) перечисление, определяющее тип конструкторов к перечислению.  
  
 `ppEnum`  
 \[out\] возвращает [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) объект, представляющий список конструкторов.  Возвращает значение NULL, если какие\-либо конструкторы.  
  
## Возвращаемое значение  
 В случае успеха возвращает значение S\_OK и возвращает значение S\_FALSE, если отсутствуют конструкторы.  В противном случае возвращает код ошибки.  
  
## Заметки  
 Каждый элемент перечисления [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) объект, описывающий метод конструктора.  
  
 Список конструкторов обычно не включает конструкторы, предоставляемые по умолчанию компилятором.  
  
## См. также  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [CONSTRUCTOR\_ENUM](../../../extensibility/debugger/reference/constructor-enum.md)
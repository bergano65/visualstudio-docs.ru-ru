---
title: "IDebugFunctionObject::CreatePrimitiveObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugFunctionObject::CreatePrimitiveObject"
helpviewer_keywords: 
  - "Метод IDebugFunctionObject::CreatePrimitiveObject"
ms.assetid: 6e9dc8b6-b4e1-4abf-b6e0-e885910775bc
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugFunctionObject::CreatePrimitiveObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Создает упрощенный объект данных, например простое целое число.  
  
## Синтаксис  
  
```cpp#  
HRESULT CreatePrimitiveObject(   
   OBJECT_TYPE    ot,  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int CreatePrimitiveObject(  
   enum_OBJECT_TYPE ot,   
   out IDebugObject ppObject  
);  
```  
  
#### Параметры  
 `ot`  
 \[in\] значение из [OBJECT\_TYPE](../../../extensibility/debugger/reference/object-type.md) перечисление, представляющее тип примитива, чтобы создать.  
  
 `ppObject`  
 \[out\] возвращает IDebugObject представления вновь созданный объект.  
  
## Возвращаемое значение  
 В случае успеха возвращает значение S\_OK; в противном случае возвращает код ошибки.  
  
## Заметки  
 Вызовите этот метод, чтобы создать объект, который представляет упрощенный объект, параметр функции, которая представлена IDebugFunctionObject интерфейс.  Например, если строка выражения "myString \(5\)", этот метод будет использоваться для создания объект, представляющий целое число 5.  
  
## См. также  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
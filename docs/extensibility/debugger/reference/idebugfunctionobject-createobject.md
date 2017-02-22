---
title: "IDebugFunctionObject::CreateObject | Microsoft Docs"
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
  - "IDebugFunctionObject::CreateObject"
helpviewer_keywords: 
  - "Метод IDebugFunctionObject::CreateObject"
ms.assetid: c4c99dd5-609a-4e7c-8f29-eb728f57e995
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugFunctionObject::CreateObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Создает объект с помощью конструктора.  
  
## Синтаксис  
  
```cpp#  
HRESULT CreateObject(   
   IDebugFunctionObject* pConstructor,  
   DWORD                 dwArgs,  
   IDebugObject*         pArgs[],  
   IDebugObject**        ppObject  
);  
```  
  
```c#  
int CreateObject(  
   IDebugFunctionObject pConstructor,   
   uint                 dwArgs,   
   IDebugObject[]       pArgs,   
   out IDebugObject     ppObject  
);  
```  
  
#### Параметры  
 `pConstructor`  
 \[in\] IDebugFunctionObject объект, представляющий конструктор объекта, который необходимо создать.  
  
 `dwArgs`  
 \[in\] количество параметров`pArg` массив.  Представляет количество параметров, передаваемых в конструктор.  
  
 `pArg`  
 \[in\] массив IDebugObject объекты, представляющих параметры, передаваемые конструктору.  
  
 `ppObject`  
 \[out\] возвращает `IDebugObject` представления вновь созданный объект.  
  
## Возвращаемое значение  
 В случае успеха возвращает значение S\_OK; в противном случае возвращает код ошибки.  
  
## Заметки  
 Вызовите этот метод, чтобы создать объект, представляющий экземпляр класса \(или другого сложного типа, который требуется конструктор\), что параметр функции, которая представлена IDebugFunctionObject интерфейс.  
  
 Если параметр объекта не требует разработки, вызовите [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md) метод.  
  
## См. также  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)   
 [CreateObjectNoConstructor](../../../extensibility/debugger/reference/idebugfunctionobject-createobjectnoconstructor.md)
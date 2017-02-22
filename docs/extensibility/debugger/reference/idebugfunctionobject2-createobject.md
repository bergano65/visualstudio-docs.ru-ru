---
title: "IDebugFunctionObject2::CreateObject | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugFunctionObject2::CreateObject"
  - "CreateObject"
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugFunctionObject2::CreateObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Создает объект, который использует конструктор заданным параметры вычислений и пометить значение времени ожидания.  
  
## Синтаксис  
  
```cpp#  
HRESULT CreateObject (  
   IDebugFunctionObject* pConstructor,  
   DWORD                 dwArgs,  
   IDebugObject*         pArgs[],  
   DWORD                 dwEvalFlags,  
   DWORD                 dwTimeout,  
   IDebugObject**        ppObject  
);  
```  
  
```c#  
int CreateObject (  
   IDebugFunctionObject pConstructor,  
   uint                 dwArgs,  
   IDebugObject[]       pArgs,  
   uint                 dwEvalFlags,  
   uint                 dwTimeout,  
   out IDebugObject**   ppObject  
);  
```  
  
#### Параметры  
 `pConstructor`  
 \[in\] IDebugFunctionObject объект, представляющий конструктор объекта, который необходимо создать.  
  
 `dwArgs`  
 \[in\] количество параметров `pArg` массив.  Представляет количество параметров, передаваемых в конструктор.  
  
 `pArgs`  
 \[in\] массив IDebugObject объекты, которое представляет параметры, передаваемые конструктору.  
  
 `dwEvalFlags`  
 \[in\] сочетание пометит из [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) перечисление, указывающее как вычисление, которое нужно выполнить.  
  
 `dwTimeout`  
 \[in\] максимальное время, в миллисекундах, ожидания возврата из этого метода.  Используйте **Бесконечно** ждать бесконечно.  
  
 `ppObject`  
 \[out\] возвращает IDebugObject представления вновь созданный объект.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Вызовите этот метод, чтобы создать объект, представляющий экземпляр класса или другой сложный тип, который требуется конструктор, параметр.  
  
## См. также  
 [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
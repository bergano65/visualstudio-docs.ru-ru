---
title: "IDebugFunctionObject::CreateArrayObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugFunctionObject::CreateArrayObject"
helpviewer_keywords: 
  - "Метод IDebugFunctionObject::CreateArrayObject"
ms.assetid: a380e53c-15f1-401f-927f-f366eea789e6
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugFunctionObject::CreateArrayObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Создает объект массива.  Этот массив может содержать значения примитивов или экземпляра объекта.  
  
## Синтаксис  
  
```cpp#  
HRESULT CreateArrayObject(   
   OBJECT_TYPE    ot,  
   IDebugField*   pClassField,  
   DWORD          dwRank,  
   DWORD          dwDims[],  
   DWORD          dwLowBounds[],  
   IDebugObject** ppObject  
);  
```  
  
```c#  
int CreateArrayObject(  
   enum_OBJECT_TYPE ot,   
   IDebugField      pClassField,   
   uint             dwRank,   
   uint[]           dwDims,   
   uint[]           dwLowBounds,   
   out IDebugObject ppObject  
);  
```  
  
#### Параметры  
 `ot`  
 \[in\] определяет значение [OBJECT\_TYPE](../../../extensibility/debugger/reference/object-type.md) перечисление, представляющее тип нового объекта массива.  
  
 `pClassField`  
 \[in\] IDebugField объект, представляющий класс объекта, если создать массив значений экземпляра объекта.  Если создать массив объектов, типов\-примитивов этого параметра значение NULL.  
  
 `dwRank`  
 \[in\] рядов или число измерений массива.  
  
 `dwDims`  
 \[in\] размер каждого измерения массива.  
  
 `dwLowBounds`  
 \[in\] начало координат каждого измерения \(обычно 0 или 1\).  
  
 `ppObject`  
 \[out\] возвращает IDebugObject объект, представляющий созданный массив.  Это фактически [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) объект.  
  
## Возвращаемое значение  
 В случае успеха возвращает значение S\_OK; в противном случае возвращает код ошибки.  
  
## Заметки  
 Вызовите этот метод, чтобы создать объект, представляющий параметр массива на функцию, представленную IDebugFunctionObject интерфейс.  
  
## См. также  
 [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
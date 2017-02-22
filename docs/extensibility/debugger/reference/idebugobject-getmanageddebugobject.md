---
title: "IDebugObject::GetManagedDebugObject | Microsoft Docs"
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
  - "IDebugObject::GetManagedDebugObject"
helpviewer_keywords: 
  - "Метод IDebugObject::GetManagedDebugObject"
ms.assetid: cb89692e-7657-47ff-846d-311943521951
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugObject::GetManagedDebugObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Создает копию управляемого объекта в адресном пространстве обработчика отладки.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetManagedDebugObject(   
   IDebugManagedObject** ppObject  
);  
```  
  
```c#  
int GetManagedDebugObject(  
   out IDebugManagedObject ppObject  
);  
```  
  
#### Параметры  
 `ppObject`  
 \[out\] возвращает [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) объект, представляющий созданный управляемый объект.  
  
## Возвращаемое значение  
 В случае успеха возвращает значение S\_OK; в противном случае возвращает код ошибки.  Возвращает E\_FAIL, если данное IDebugObject не представляет управляемый экземпляр класса значения.  
  
## Заметки  
 This [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) объект должен представить управляемый экземпляр класса значения, например, a  `System.Decimal` экземпляр.  Путем иметь локальную копию, издержки вызова [Оценка](../../../extensibility/debugger/reference/idebugfunctionobject-evaluate.md) исключает.  
  
## См. также  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)   
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
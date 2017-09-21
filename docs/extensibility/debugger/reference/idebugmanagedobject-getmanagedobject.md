---
title: "IDebugManagedObject::GetManagedObject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugManagedObject::GetManagedObject"
helpviewer_keywords: 
  - "Метод IDebugManagedObject::GetManagedObject"
ms.assetid: 6abe1402-6aad-41e6-8ec1-ae12d5945992
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugManagedObject::GetManagedObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает интерфейс, представляющий управляемый объект.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetManagedObject(   
   IUnknown** ppManagedObject  
);  
```  
  
```cpp#  
int GetManagedObject(  
   out object ppManagedObject  
);  
```  
  
#### Параметры  
 `ppManagedObject`  
 \[out\] возвращает интерфейс, представляющий управляемый объект.  
  
## Возвращаемое значение  
 В случае успеха возвращает значение S\_OK; в противном случае возвращает код ошибки.  
  
## Заметки  
 Интерфейс, возвращаемый из этого метода можно запросить для любого интерфейса, реализованного управляемым классом, позволяя его методы для вызова.  
  
## См. также  
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
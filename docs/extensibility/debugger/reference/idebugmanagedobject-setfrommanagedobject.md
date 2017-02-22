---
title: "IDebugManagedObject::SetFromManagedObject | Microsoft Docs"
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
  - "IDebugManagedObject::SetFromManagedObject"
helpviewer_keywords: 
  - "Метод IDebugManagedObject::SetFromManagedObject"
ms.assetid: 8700ee8d-2704-4580-bccc-046837a24edd
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugManagedObject::SetFromManagedObject
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Задает значение экземпляра объекта класса значения из экземпляра предоставленного класса значения в качестве параметра.  
  
## Синтаксис  
  
```cpp#  
HRESULT SetFromManagedObject(   
   IUnknown* pManagedObject  
);  
```  
  
```c#  
int SetFromManagedObject(  
   object pManagedObject  
);  
```  
  
#### Параметры  
 `pManagedObject`  
 \[in\] интерфейс, который представляет управляемый объект, содержащий новое значение.  
  
## Возвращаемое значение  
 В случае успеха возвращает значение S\_OK; в противном случае возвращает код ошибки.  
  
## Заметки  
 Этот метод используется для изменения в виде управляемый объект [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md) объект.  
  
## См. также  
 [IDebugManagedObject](../../../extensibility/debugger/reference/idebugmanagedobject.md)
---
title: "IDebugPortSupplier2::CanAddPort | Microsoft Docs"
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
  - "IDebugPortSupplier2::CanAddPort"
helpviewer_keywords: 
  - "IDebugPortSupplier2::CanAddPort"
ms.assetid: 41f69e0a-e82c-473d-8b7a-0c40fc5730fc
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugPortSupplier2::CanAddPort
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Проверяет, что поставщик порта может добавлять новые порты.  
  
## Синтаксис  
  
```cpp#  
HRESULT CanAddPort(   
   void   
);  
```  
  
```c#  
int CanAddPort();  
```  
  
## Возвращаемое значение  
 Если порт может быть добавлен; возвращает `S_OK`; в противном случае возвращает  `S_FALSE` не указывать никаких порты можно добавить к данному поставщику порта.  
  
## Заметки  
 Этот метод следует вызывать перед вызовом [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md) метод с момента последнего метод создает порт, а также добавляют его, может оказаться длительной операцией.  
  
## См. также  
 [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [AddPort](../../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
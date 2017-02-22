---
title: "IDebugProgramPublisher2::UnpublishProgram | Microsoft Docs"
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
  - "IDebugProgramPublisher2::UnpublishProgram"
helpviewer_keywords: 
  - "IDebugProgramPublisher2::UnpublishProgram"
ms.assetid: 627e7d38-b2ac-4873-9a40-37ff7f47cd1d
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramPublisher2::UnpublishProgram
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Сделать программу недоступной быть отлаживанным.  
  
## Синтаксис  
  
```cpp  
HRESULT UnpublishProgram(  
   IUnknown* pDebuggeeInterface  
);  
```  
  
```c#  
int UnpublishProgram(  
   object pDebuggeeInterface  
);  
```  
  
#### Параметры  
 `pDebuggeeInterface`  
 \[in\] `IUnknown` интерфейс для программы.  Это то же значение, передаваемое [PublishProgram](../Topic/IDebugProgramPublisher2::PublishProgram.md) метод и однозначно определяющее удаляемый программы \(т е он используется как cookie\).  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Чтобы сделать доступными программы к обработчикам отладки и сеансу отладки, используйте диспетчер [PublishProgram](../Topic/IDebugProgramPublisher2::PublishProgram.md) метод.  
  
## См. также  
 [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)   
 [PublishProgram](../Topic/IDebugProgramPublisher2::PublishProgram.md)
---
title: "IDebugProperty3::CreateObjectID | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty3::CreateObjectID"
helpviewer_keywords: 
  - "IDebugProperty3::CreateObjectID"
ms.assetid: f2fa81e7-822f-456e-8729-a96a18eea771
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProperty3::CreateObjectID
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Создает уникальный идентификатор для этого свойства, чтобы убедиться, что оно уникальным среди всех остальных свойств.  
  
## Синтаксис  
  
```cpp  
HRESULT CreateObjectID(  
   void  
);  
```  
  
```c#  
int CreateObjectID();  
```  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Этот метод вызывается, когда сеанс отладки диспетчер необходимо убедиться в том, что это свойство однозначно определяется среди всех других свойств.  Отладчик \(DE\) поддерживает этот метод, если свойства он имеет дело с уже определен однозначно.  Если DE не поддерживает этот метод, он возвращает `E_NOTIMPL`.  
  
 Уникальный идентификатор, созданный с любой `CreateObjectID` когда удаляется  [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md) метод вызывается; это также отмечающий конец мере необходимости для уникального определения это свойство.  
  
> [!NOTE]
>  Ни один метод для извлечения этот уникальный идентификатор, поэтому DE может выполнять любые действия, если он желает для уникальных идентификаторов `CreateObjectID` вызывается метод.  
  
## См. также  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [DestroyObjectID](../../../extensibility/debugger/reference/idebugproperty3-destroyobjectid.md)
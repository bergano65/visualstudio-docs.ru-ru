---
title: "IDebugProperty3::DestroyObjectID | Microsoft Docs"
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
  - "IDebugProperty3::DestroyObjectID"
helpviewer_keywords: 
  - "IDebugProperty3::DestroyObjectID"
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProperty3::DestroyObjectID
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Уничтожает уникальный идентификатор, связанный с это свойство, указывающее, что вызывающий не имеет значения, чтобы определить это свойство однозначно от всех остальных свойств.  
  
## Синтаксис  
  
```cpp  
HRESULT DestroyObjectID(  
   void  
);  
```  
  
```c#  
int DestroyObjectID();  
```  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Если обработчик отладки не требуется поддерживать уникальных идентификаторов для свойства \(потому что он уже отслеживает их уникальными внутри\), он может просто возвращать `E_NOTIMPL` для данного метода.  
  
 Уникальные идентификаторы создаются с вызовом [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) когда вызывающий метод необходимо убедиться в том, что это свойство однозначно определяется среди всех других свойств.  
  
## См. также  
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)
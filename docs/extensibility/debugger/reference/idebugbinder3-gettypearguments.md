---
title: "IDebugBinder3::GetTypeArguments | Microsoft Docs"
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
  - "IDebugBinder3::GetTypeArguments"
helpviewer_keywords: 
  - "Метод IDebugBinder3::GetTypeArguments"
ms.assetid: fa0c37a7-327f-463e-9a9d-bb3f534584cb
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBinder3::GetTypeArguments
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот метод извлекает список типов аргументов, связанных с этим объектом.  
  
## Синтаксис  
  
```cpp  
HRESULT GetTypeArguments(  
   UINT          skip,  
   UINT          count,  
   IDebugField** ppFields,  
   UINT*         pFetched  
);  
```  
  
```c#  
int GetTypeArguments(  
   uint          skip,  
   uint          count,  
   IDebugField[] ppFields,  
   out uint      pFetched  
);  
```  
  
#### Параметры  
 `skip`  
 \[in\] число полей, которые необходимо пропустить перед получением типы аргументов.  
  
 `count`  
 \[in\] число полей аргумента, который требуется вернуть \(также определяет размер `ppFields` массив\).  
  
 `ppFields`  
 \[in, out\] массив полей, которые будут заполняются при возврате данного метода.  
  
 `pFetched`  
 \[out\] \(необязательно\) количество фактически, возвращенных полей типа аргумента.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Количество типов аргументов можно получить с заранее [GetTypeArgumentCount](../Topic/IDebugBinder3::GetTypeArgumentCount.md).  
  
## См. также  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [GetTypeArgumentCount](../Topic/IDebugBinder3::GetTypeArgumentCount.md)
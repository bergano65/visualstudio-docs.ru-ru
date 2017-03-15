---
title: "IDebugAlias2::GetAppDomainId | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "GetAppDomainId"
  - "IDebugAlias2::GetAppDomainId"
ms.assetid: 23581aaa-5a53-4859-b264-eca49fc44bcd
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugAlias2::GetAppDomainId
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Извлекает идентификатор для домена приложения.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetAppDomainId (  
   ULONG32* pappDomainId  
);  
```  
  
```c#  
int GetAppDomainId (  
   out uint pappDomainId  
);  
```  
  
#### Параметры  
 `pappDomainId`  
 \[out\] возвращает идентификатор домена приложения.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Идентификатор домена приложения изменяется, когда приложение перезапускается и новый домен приложения создается.  
  
## См. также  
 [IDebugAlias2](../../../extensibility/debugger/reference/idebugalias2.md)
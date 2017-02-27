---
title: "IDebugBinder3::FindAlias | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder3::FindAlias"
helpviewer_keywords: 
  - "Метод IDebugBinder3::FindAlias"
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugBinder3::FindAlias
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот метод находит псевдоним по имени.  Это будет искать все псевдонимы в программе.  
  
## Синтаксис  
  
```cpp  
HRESULT FindAlias(  
   LPCOLESTR     pcstrName,  
   IDebugAlias** ppAlias  
);  
```  
  
```c#  
int FindAlias(  
   string          pcstrName,  
   out IDebugAlias ppAlias  
);  
```  
  
#### Параметры  
 `pcstrName`  
 \[in\] имя псевдонима для поиска.  
  
 `ppAlias`  
 \[out\] псевдоним обнаружил \(если таковые имеются\), представленное [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) интерфейс.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает  `S_FALSE` \(если псевдоним не найден\) или код ошибки.  
  
## Заметки  
 Этот метод инициализирует объект назначения перед вызовом; в null затем он проверяет значение NULL для того, чтобы определить, был ли найден или не псевдоним.  
  
## См. также  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)   
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
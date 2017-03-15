---
title: "IDebugObject2::IsUserData | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject2::IsUserData"
helpviewer_keywords: 
  - "Метод IDebugObject2::IsUserData"
ms.assetid: 6ffa0d0e-f742-496d-acc7-db74c248bc45
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugObject2::IsUserData
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Определяет, представляет ли объект пользователей.  
  
## Синтаксис  
  
```cpp  
HRESULT IsUserData(  
   BOOL* pfUser  
);  
```  
  
```c#  
int IsUserData(  
   out int pfUser  
);  
```  
  
#### Параметры  
 `pfUser`  
 \[out\] возвращает ненулевое \(`TRUE`если объект представляет пользователей; ноль \(`FALSE`\), если нет.  
  
## Возвращаемое значение  
 В случае успеха возвращает значение S\_OK; в противном случае возвращает код ошибки.  
  
## Заметки  
 Пользователь любой объект, являющийся частью модуля, обозначенного как JustMyCode \(пользователь\-конфигурируемый параметр, который указывает модуль как код пользователя и поэтому видимый в трассировке стека\).  
  
## См. также  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
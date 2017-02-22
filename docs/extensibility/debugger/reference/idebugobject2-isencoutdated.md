---
title: "IDebugObject2::IsEncOutdated | Microsoft Docs"
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
  - "IDebugObject2::IsEncOutdated"
helpviewer_keywords: 
  - "Метод IDebugObject2::IsEncOutdated"
ms.assetid: d3a8c02d-895b-478c-9957-d663130f308e
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugObject2::IsEncOutdated
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот метод определяет, является ли правка и продолжает состояние этого объекта или родительского контейнера устарели.  Настраиваемое средство оценки выражений этот метод не реализован и всегда возвращает `E_NOTIMPL`.  
  
## Синтаксис  
  
```cpp  
HRESULT IsEncOutdated(  
   BOOL* pfEncOutdated  
);  
```  
  
```c#  
int IsEncOutdated(  
   out int pfEncOutdated  
);  
```  
  
#### Параметры  
 `pfEncOutdated`  
 \[out\] ненулевое значение \(`TRUE`если правка и переход состояния устарела, ноль \(`FALSE`если она не найдена.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
> [!NOTE]
>  Настраиваемое средство оценки выражений должно всегда возвращать `E_NOTIMPL`.  
  
## См. также  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
---
title: "IDebugArrayField::GetRank | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugArrayField::GetRank"
helpviewer_keywords: 
  - "Метод IDebugArrayField::GetRank"
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugArrayField::GetRank
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает ряды или число измерений массива.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetRank(   
   DWORD* pdwRank  
);  
```  
  
```c#  
int GetRank(  
   out uint pdwRank  
);  
```  
  
#### Параметры  
 `pdwRank`  
 \[out\] возвращает ряд.  
  
## Возвращаемое значение  
 В случае успеха возвращает значение S\_OK; в противном случае возвращает код ошибки.  
  
## Заметки  
 Ряды массива соответствует количеству измерений.  В C\+\+ и c\#, индексация многомерных массивов являются массивы массивов и поэтому могут рассматриваться как одномерный массив \(и `GetRank` метод всегда возвращает 1\).  IN [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]с другой стороны, многомерный массив обрабатываются и ряды такого массива отражает количество измерений \(и  `GetRank` метод всегда возвращает количество измерений\).  
  
## См. также  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)
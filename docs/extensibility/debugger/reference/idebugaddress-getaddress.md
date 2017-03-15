---
title: "IDebugAddress::GetAddress | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugAddress::GetAddress"
helpviewer_keywords: 
  - "Метод IDebugAddress:GetAddress"
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugAddress::GetAddress
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает структуру, описывающий объект и его расположение в его области или контейнера.  
  
## Синтаксис  
  
```cpp  
HRESULT GetAddress (  
   DEBUG_ADDRESS * pAddress  
);  
```  
  
```c#  
int GetAddress(  
   DEBUG_ADDRESS[] pAddress  
);  
```  
  
#### Параметры  
 `pAddress`  
 \[in, out\] a [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) структура, заполняемую этим методом.  
  
## Возвращаемое значение  
 В случае успеха возвращает значение S\_OK; в противном случае возвращает код ошибки.  
  
## Заметки  
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) структура передается этому методу, который затем заполняет его с соответствующим сведения.  Интерпретируются как эти сведения зависят от возвращаемого сам тип сведений и обработчика символов.  Дополнительные сведения см. в разделе [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md).  
  
## См. также  
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)
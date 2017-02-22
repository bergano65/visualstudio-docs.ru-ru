---
title: "IDebugObject::GetValue | Microsoft Docs"
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
  - "IDebugObject::GetValue"
helpviewer_keywords: 
  - "Метод IDebugObject::GetValue"
ms.assetid: eec6051e-8ecb-49fa-bdd4-dd786f211692
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugObject::GetValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает значение объекта, как последовательный последовательность байтов.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetValue(   
   BYTE* pValue,  
   UINT  nSize  
);  
```  
  
```c#  
int GetValue(  
   ref byte[] pValue,   
   uint nSize  
);  
```  
  
#### Параметры  
 `pValue`  
 \[in, out\] массив, который заполняется с последовательным рядом байтов, представляющий значение объекта.  
  
 `nSize`  
 \[in\] максимальное количество байтов, которое необходимо извлечь.  
  
## Возвращаемое значение  
 В случае успеха возвращает значение S\_OK; в противном случае возвращает код ошибки.  
  
## Заметки  
 Возвращает общее количество байтов значения, которые могут быть получены путем вызова [GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md) метод.  
  
## См. также  
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
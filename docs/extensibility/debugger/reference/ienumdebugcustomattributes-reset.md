---
title: "IEnumDebugCustomAttributes::Reset | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumCustomAttributes::Reset"
helpviewer_keywords: 
  - "IEnumDebugCustomAttributes::Reset"
ms.assetid: e0db6518-5a71-4adb-a407-4d2ac7a3e369
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IEnumDebugCustomAttributes::Reset
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Сбрасывает последовательность перечисления в начало.  
  
## Синтаксис  
  
```cpp#  
HRESULT Reset(void);  
```  
  
```c#  
int Reset();  
```  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 После вызова этого метода, следующий вызов [Далее](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md) метод возвращает первый элемент перечисления.  
  
## См. также  
 [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)   
 [Далее](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)
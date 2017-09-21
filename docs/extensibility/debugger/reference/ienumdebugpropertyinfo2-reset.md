---
title: "IEnumDebugPropertyInfo2::Reset | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumDebugPropertyInfo2::Reset"
helpviewer_keywords: 
  - "IEnumDebugPropertyInfo2::Reset"
ms.assetid: fa4201c1-4633-4596-93aa-bd415c4ed71a
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEnumDebugPropertyInfo2::Reset
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Сбросит перечисление к первому элементу.  
  
## Синтаксис  
  
```cpp#  
HRESULT Reset(  
   void  
);  
```  
  
```c#  
int Reset();  
```  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 После вызова этого метода, следующий вызов [Далее](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-next.md) метод возвращает первый элемент перечисления.  
  
## См. также  
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
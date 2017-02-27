---
title: "IEnumCodePaths2::Reset | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEnumCodePaths2::Reset"
helpviewer_keywords: 
  - "IEnumCodePaths2::Reset"
ms.assetid: 490c0e19-ff4b-4673-bd06-cdee996ac226
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IEnumCodePaths2::Reset
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
 После вызова этого метода, следующий вызов [Далее](../../../extensibility/debugger/reference/ienumcodepaths2-next.md) метод возвращает первый элемент перечисления.  
  
## См. также  
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)
---
title: "IDebugBinder3::GetExceptionObjectAndType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugBinder3::GetExceptionObjectAndType"
helpviewer_keywords: 
  - "Метод IDebugBinder3::GetExceptionObjectAndType"
ms.assetid: 2a313fe1-4ee1-4f01-af86-382d6c661a8f
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugBinder3::GetExceptionObjectAndType
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот метод возвращает исключение, связанное с объектом, если таковые имеются.  
  
## Синтаксис  
  
```cpp  
HRESULT GetExceptionObjectAndType(  
   IDebugObject** ppException,  
   IDebugField**  ppField  
);  
```  
  
```c#  
int GetExceptionObjectAndType(  
   out IDebugObject ppException,  
   out IDebugField  ppField  
);  
```  
  
#### Параметры  
 `ppException`  
 \[out\] возвращает объект, представляющий исключение.  
  
 `ppField`  
 \[out\] возвращает объект, представляющий указанное поле, которое может вызвать исключение \(это может быть значение NULL\).  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
> [!NOTE]
>  Для проверки, является ли исключение, проверьте значение, возвращаемое оператором `ppException`. если задано значение NULL, то исключение не связанное с этим объектом.  
  
## См. также  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
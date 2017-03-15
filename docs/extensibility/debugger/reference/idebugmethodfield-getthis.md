---
title: "IDebugMethodField::GetThis | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField::GetThis"
helpviewer_keywords: 
  - "Метод IDebugMethodField::GetThis"
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugMethodField::GetThis
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает `this` \(`Me` IN  [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]указатель объекта, содержащий метод.\)  
  
## Синтаксис  
  
```cpp#  
HRESULT GetThis(   
   IDebugClassField** ppClass  
);  
```  
  
```c#  
int GetThis(  
   out IDebugClassField ppClass  
);  
```  
  
#### Параметры  
 `ppClass`  
 \[out\] возвращает [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) объект, представляющий этот указатель "".  
  
## Возвращаемое значение  
 В случае успеха возвращает значение S\_OK; в противном случае возвращает код ошибки.  
  
## Заметки  
 В объект\-ориентированных языках, обычно неявный указатель на текущий экземпляр класса.  Как `this` в C\#\/C\+\+ и как  `Me` IN  [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)].  
  
## См. также  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
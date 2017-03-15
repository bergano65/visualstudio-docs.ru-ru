---
title: "IDebugEngine3::LoadSymbols | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine3::LoadSymbols"
helpviewer_keywords: 
  - "IDebugEngine3::LoadSymbols"
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugEngine3::LoadSymbols
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Загружает \(при необходимости\) символов для всех модулей, отлаживанными этим обработчиком отладки.  
  
## Синтаксис  
  
```cpp  
HRESULT LoadSymbols();  
```  
  
```c#  
int LoadSymbols();  
```  
  
#### Параметры  
 Отсутствует.  
  
## Возвращаемое значение  
 В случае успеха возвращает значение S\_OK; в противном случае возвращает код ошибки.  
  
## Заметки  
 Это загружает символы отладки для всех модулей, на которые ссылается этим обработчиком отладки.  Они загружаются только в том случае, если они еще не загружены.  Символы производится в путях задаются вызовом [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md).  
  
## См. также  
 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
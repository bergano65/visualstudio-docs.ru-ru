---
title: "IDebugProcess3::DisableENC | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProcess3::DisableENC"
helpviewer_keywords: 
  - "IDebugProcess3::DisableENC"
ms.assetid: cffdbdac-4d76-4aeb-aa55-5d0410db99f1
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugProcess3::DisableENC
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот метод явным образом запрещает правку и продолжается в этом процессе \(и все программы в нем содержатся\).  Пользовательский поставщик порта должен всегда возвращать `E_NOTIMPL`.  
  
## Синтаксис  
  
```cpp  
HRESULT DisableENC(  
   EncUnavailableReason reason  
);  
```  
  
```c#  
   EncUnavailableReason reason  
);  
```  
  
#### Параметры  
 `reason`  
 \[in\] значение из [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md) перечисление.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
> [!NOTE]
>  Пользовательский поставщик порта должен всегда возвращать `E_NOTIMPL`.  
  
## Заметки  
 Кнопка продолжить только правку и заблокированы для процесса, могут быть разрешены только путем запуска процесса.  
  
## См. также  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [EncUnavailableReason](../../../extensibility/debugger/reference/encunavailablereason.md)
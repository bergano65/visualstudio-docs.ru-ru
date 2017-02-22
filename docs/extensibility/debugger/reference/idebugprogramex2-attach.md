---
title: "IDebugProgramEx2::Attach | Microsoft Docs"
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
  - "IDebugProgramEx2::Attach"
helpviewer_keywords: 
  - "IDebugProgramEx2::Attach"
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgramEx2::Attach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Вложите сеанс в программе.  
  
## Синтаксис  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason,  
   IDebugSession2*       pSession  
);  
```  
  
```  
[C#]  
int Attach(   
   IDebugEventCallback2 pCallback,  
   uint                 dwReason,  
   IDebugSession2       pSession  
);  
```  
  
#### Параметры  
 `pCallback`  
 \[in\] IDebugEventCallback2 объект, который представляет функцию обратного вызова, что вложенные обработчик отладки отправляет события.  
  
 `dwReason`  
 \[in\] значение из [ATTACH\_REASON](../../../extensibility/debugger/reference/attach-reason.md) перечисление, описывающее причину для операции присоединения.  
  
 `pSession`  
 \[in\] значение, уникально определяющее сеанс, вложение в программе.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  Этот метод должен возвращать `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` если программа уже вложенна.  
  
## Заметки  
 Порт, который содержит программу может использовать значение в пределах `pSession` определить, какой сеанс пытается вложить в программе.  Например, если порт разрешает только один сеанс отладки, чтобы вложение в процесс, если один и тот же порт может определить сеанс уже вложен в другой программы в процессе.  
  
> [!NOTE]
>  Интерфейс переданный `pSession` должна рассматриваться только как файл cookie, значение, уникально определяющее сеанс отладки диспетчер вложа в этой программе; ни один из методов в интерфейсе, предоставляемом функциональны.  
  
## См. также  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)
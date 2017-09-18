---
title: "IDebugCoreServer3::EnableAutoAttach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer3::EnableAutoAttach"
helpviewer_keywords: 
  - "IDebugCoreServer3::EnableAutoAttach"
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugCoreServer3::EnableAutoAttach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Включает автоматический вложить обработчики для указанного debug.  
  
## Синтаксис  
  
```cpp#  
HRESULT EnableAutoAttach(  
   GUID*     rgguidSpecificEngines,  
   DWORD     celtSpecificEngines,  
   LPCOLESTR pszStartPageUrl,  
   BSTR*     pbstrSessionId  
);  
```  
  
```c#  
int EnableAutoAttach(  
   Guid[]     rgguidSpecificEngines,  
   uint       celtSpecificEngines,  
   string     pszStartPageUrl,  
   out string pbstrSessionId  
);  
```  
  
#### Параметры  
 `rgguidSpecificEngines`  
 \[in\] массив идентификаторов GUID для каждого обработчика отладки, чтобы пометить как автоматическ\-вложащ.  
  
 `celtSpecificEngines`  
 \[in\] число обработчиков, определенных в пределах `rgguidSpecificEngines`.  
  
 `pszStartPageUrl`  
 \[in\] начальный URL\-адрес, используемый автоматическ\-вложа.  
  
 `pbstrSessionID`  
 \[out\] идентификатор сеанса, который был вложен.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  Один код ошибки `E_AUTO_ATTACH_NOT_REGISTERED`означает, что не была зарегистрирована фабрика класса автоматическ\-вложить.  
  
## Заметки  
 При запуске программа, связанная с указанным url\-адресом, заданные обработчики отладки автоматически запускаются и вложенные.  
  
## См. также  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
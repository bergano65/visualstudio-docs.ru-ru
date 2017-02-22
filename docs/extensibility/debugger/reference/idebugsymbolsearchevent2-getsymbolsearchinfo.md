---
title: "IDebugSymbolSearchEvent2::GetSymbolSearchInfo | Microsoft Docs"
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
  - "IDebugSymbolSearchEvent2::GetSymbolSearchInfo"
helpviewer_keywords: 
  - "IDebugSymbolSearchEvent2::GetSymbolSearchInfo"
ms.assetid: ae9eb72b-f2aa-43b8-87ca-da19d2e78d17
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSymbolSearchEvent2::GetSymbolSearchInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Вызывается обработчиком событий для получения результатов о процессе загрузки символов.  
  
## Синтаксис  
  
```cpp  
HRESULT GetSymbolSearchInfo(  
   IDebugModule3**    pModule,  
   BSTR*              pbstrDebugMessage,  
   MODULE_INFO_FLAGS* pdwModuleInfoFlags  
);  
```  
  
```c#  
int GetSymbolSearchInfo(  
   IDebugModule3              pModule,   
   ref string                 pbstrDebugMessage,   
   out enum_MODULE_INFO_FLAGS pdwModuleInfoFlags  
);  
  
```  
  
#### Параметры  
 `pModule`  
 \[out\] объект IDebugModule3, представляющий модуль, для которого были загружены символы.  
  
 `pbstrDebugMessage`  
 \[in, out\] возвращает строку, содержащую все сообщения об ошибках из модуля.  Если ошибка, то эта строка будет содержать только имя модуля, но она никогда не пуста.  
  
> [!NOTE]
>  \[C\+\+\] `pbstrDebugMessage` не удается  `NULL` и быть освобожено с  `SysFreeString`.  
  
 `pdwModuleInfoFlags`  
 \[out\] сочетание пометит из [MODULE\_INFO\_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md) перечисление, указывающее были загружены ли какие\-либо символы.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Когда обработчик возвращает [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) событие после попытке загрузить символы отладки для модуля, обработчик может вызвать thismethod, чтобы определить результаты этой загрузки.  
  
## См. также  
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)   
 [MODULE\_INFO\_FLAGS](../../../extensibility/debugger/reference/module-info-flags.md)   
 [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md)
---
title: "IDebugSymbolProvider::GetAddressesFromContext | Microsoft Docs"
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
  - "IDebugSymbolProvider::GetAddressesFromContext"
helpviewer_keywords: 
  - "Метод IDebugSymbolProvider::GetAddressesFromContext"
ms.assetid: a3124883-a255-4543-a5ec-e1c7a97beb69
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSymbolProvider::GetAddressesFromContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот метод сопоставляет контекст рисования в массив адресов отладки.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetAddressesFromContext(   
   IDebugDocumentContext2* pDocContext,  
   BOOL                    fStatmentOnly,  
   IEnumDebugAddresses**   ppEnumBegAddresses,  
   IEnumDebugAddresses**   ppEnumEndAddresses  
);  
```  
  
```c#  
int GetAddressesFromContext(  
   IDebugDocumentContext2  pDocContext,  
   bool                    fStatmentOnly,  
   out IEnumDebugAddresses ppEnumBegAddresses,  
   out IEnumDebugAddresses ppEnumEndAddresses  
);  
```  
  
#### Параметры  
 `pDocContext`  
 \[in\] контекст рисования.  
  
 `fStatmentOnly`  
 \[in\] если задано значение true, то ограничения, то отладку обращается к одному выписке.  
  
 `ppEnumBegAddresses`  
 \[out\] возвращает перечислитель для запуска отладки адреса, связанные с этими выпиской или линией.  
  
 `ppEnumEndAddresses`  
 \[out\] возвращает [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) перечислитель для отладки конечного адреса, связанные с этими выпиской или линией.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Контекст рисования обычно указывает диапазон линий источника.  Этот метод обеспечивает запуск и завершение отладка адреса, связанные с этими линиями.  Некоторые языки позволяют выписки, что диапазон несколько линий или линий, который содержит несколько выписку.  Этот метод предоставляет пометить для ограничения адреса отлаживать в один выписке.  
  
 Возможно, одной выписки иметь несколько отладки адреса, например в случае шаблонов.  
  
## См. также  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [GetAddressesFromPosition](../Topic/IDebugSymbolProvider::GetAddressesFromPosition.md)   
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)
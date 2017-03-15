---
title: "IDebugPortSupplier3::EnumPersistedPorts | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortSupplier3::EnumPersistedPorts"
helpviewer_keywords: 
  - "IDebugPortSupplier3::EnumPersistedPorts"
ms.assetid: 1c3dead3-5d6c-4067-8418-4015f0b0dd07
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugPortSupplier3::EnumPersistedPorts
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот метод извлекает объект, который разрешает прикрепление список сохраненных портов.  
  
## Синтаксис  
  
```cpp  
HRESULT EnumPersistedPorts(  
   BSTR_ARRAY         PortNames,  
   IEnumDebugPorts2** ppEnum  
);  
```  
  
```c#  
int EnumPersistedPorts(  
   BSTR_ARRAY           PortNames,  
   out IEnumDebugPorts2 ppEnum  
);  
```  
  
#### Параметры  
 `PortNames`  
 \[in\] значение [BSTR\_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) структура, содержащая список имен порта для поиска и возвращения из сохраненных портов.  Только как persisted порты с этими именами будет возвращено.  
  
 `ppEnum`  
 \[out\] объект, который реализует [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) интерфейс.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Загружаются, когда создается поставщик порта и хранятся постоянные порты, когда разрушают поставщика порта.  
  
## См. также  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)   
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)   
 [BSTR\_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)
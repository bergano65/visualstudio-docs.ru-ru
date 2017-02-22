---
title: "IDebugAlias::GetICorDebugValue | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugAlias::GetICorDebugValue"
helpviewer_keywords: 
  - "Метод IDebugAlias::GetICorDebugValue"
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugAlias::GetICorDebugValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Получает интерфейс управляемого кода, который представляет значение, связанное с данным псевдонимом.  
  
## Синтаксис  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```c#  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### Параметры  
 `ppUnk`  
 \[out\] `IUnknown` интерфейс, который представляет значение, связанное с данным псевдонимом. Этот интерфейс можно запрашивать `ICorDebugValue` интерфейса.  
  
## Возвращаемое значение  
 В случае успеха возвращает значение S\_OK; в противном случае возвращается код ошибки.  
  
## Заметки  
 Этот метод применим только к значениям управляемого \( `ICorDebugValue` доступен интерфейс в [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] и определен в [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] пакета SDK в файле cordebug.idl\).  
  
## См. также  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
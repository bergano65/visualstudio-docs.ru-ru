---
title: "IDebugPortSupplier3::CanPersistPorts | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortSupplier3::CanPersistPorts"
helpviewer_keywords: 
  - "IDebugPortSupplier3::CanPersistPorts"
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugPortSupplier3::CanPersistPorts
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот метод определяет, может ли поставщик порта может сохраняться портов \(путем записи их на диск\) между вызовами отладчика.  
  
## Синтаксис  
  
```cpp  
HRESULT CanPersistPorts();  
```  
  
```c#  
int CanPersistPorts();  
```  
  
#### Параметры  
 Отсутствует.  
  
## Возвращаемое значение  
 `S_OK` если порты могут быть сохранены или  `S_FALSE` показать, что порты не могут быть сохранены.  
  
## Заметки  
 Если поставщик порта может сохраняться порты, он должен сделать, когда он уничтожается, а затем перезапустите их при его создании еще раз.  
  
## См. также  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
---
title: "IEEDataStorage::GetSize | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IEEDataStorage::GetSize"
helpviewer_keywords: 
  - "IEEDataStorage::GetSize"
ms.assetid: 33d232c4-1239-4abc-922b-e1bc5b908169
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IEEDataStorage::GetSize
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Возвращает число байтов, содержащихся в этом объекте.  
  
## Синтаксис  
  
```cpp#  
HRESULT GetSize(  
   ULONG* size  
);  
```  
  
```c#  
int GetSize(  
   out uint size  
);  
```  
  
#### Параметры  
 `size`  
 \[out\] число байтов, содержащихся в этом объекте.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Используйте [GetData](../Topic/IEEDataStorage::GetData.md) метод, чтобы получить байты данных.  
  
## См. также  
 [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)   
 [GetData](../Topic/IEEDataStorage::GetData.md)
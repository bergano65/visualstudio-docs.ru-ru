---
title: "IDebugBinder3::GetAllAliases | Microsoft Docs"
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
  - "IDebugBinder3::GetAllAliases"
helpviewer_keywords: 
  - "Метод IDebugBinder3::GetAllAliases"
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugBinder3::GetAllAliases
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Этот метод извлекает список псевдонимов из программы.  
  
## Синтаксис  
  
```cpp  
HRESULT GetAllAliases(  
   UINT          uRequest,  
   IDebugAlias** ppAliases,  
   UINT*         puFetched  
);  
```  
  
```c#  
int GetAllAliases(  
   uint          uRequest,   
   IDebugAlias[] ppAliases,   
   out uint      puFetched  
);  
```  
  
#### Параметры  
 `uRequest`  
 \[in\] максимальное количество псевдонимов для возврата \(задающее длину массива в `ppAliases`\).  
  
 `ppAliases`  
 \[in, out\] массив байтов, заполняемый с псевдонимами \(если это значение равно NULL и `uRequest` 0 содержит количество псевдонимов, которые могут быть возвращены будут возвращены by  `puFetched`\).  
  
 `puFetched`  
 \[out\] возвращает число полученных псевдонимов.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## См. также  
 [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
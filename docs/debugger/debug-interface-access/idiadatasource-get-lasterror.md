---
title: "IDiaDataSource::get_lastError | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaDataSource::get_lastError - метод"
ms.assetid: cf08850b-8b75-4e8c-90bd-bd0214756f99
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaDataSource::get_lastError
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает имя файла для последней ошибки загрузки.  
  
## Синтаксис  
  
```cpp#  
HRESULT get_lastError (  
   BSTR* pRetVal  
);  
```  
  
#### Параметры  
 pRetVal  
 \[out\] возвращает строку, содержащую имя pdb\-файла, связанное с последней ошибке загрузки.  
  
## Возвращаемое значение  
 Возвращает последний код ошибки причиненный операции загрузки.  Возвращает `E_INVALIDARG` если  `pRetVal` параметр  `NULL`.  
  
## Пример  
  
```cpp#  
BSTR    fileName;  
HRESULT errorCode = pSource->get_lastError( &fileName );  
```  
  
## См. также  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
---
title: "IDiaEnumFrameData::Item | Microsoft Docs"
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
  - "IDiaEnumFrameData::Item - метод"
ms.assetid: 2761a72d-1868-4f5b-a32e-c2a1d9358c91
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumFrameData::Item
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Получает элемент данных кадра посредством индекса.  
  
## Синтаксис  
  
```cpp#  
HRESULT Item (   
   DWORD           index,  
   IDiaFrameData** section  
);  
```  
  
#### Параметры  
 индекс  
 \[in\] индекс [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) объект, который требуется извлечь.  Индекс в диапазоне от 0 до `count`\-1, где  `count` возвращает   [IDiaEnumFrameData::get\_Count](../../debugger/debug-interface-access/idiaenumframedata-get-count.md) метод.  
  
 раздел  
 \[out\] возвращает [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md) объект, представляющий требуемый элемент данных кадра.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## См. также  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)   
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)
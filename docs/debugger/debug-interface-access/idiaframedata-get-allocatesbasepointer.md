---
title: "IDiaFrameData::get_allocatesBasePointer | Microsoft Docs"
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
  - "IDiaFrameData::get_allocatesBasePointer - метод"
ms.assetid: 8a33db5d-008c-4fe5-b64f-210c9b77f686
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaFrameData::get_allocatesBasePointer
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает пометить, указывающее, выделен ли базовый указатель для кода в этом диапазоне адресов.  Этот метод является устаревшим.  
  
## Синтаксис  
  
```cpp#  
HRESULT get_allocatesBasePointer (   
   BOOL* pRetVal  
);  
```  
  
#### Параметры  
 `pRetVal`  
 \[out\] возвращает `TRUE` если базовый указатель установлен; в противном случае возвращает  `FALSE`.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`.  Возвращает `S_FALSE` если это свойство не поддерживается.  В противном случае возвращает код ошибки.  
  
## Заметки  
 Это свойство должно использоваться только кодом, который ранее был получен доступ FPO\_DATA или если строка, возвращенная программы [IDiaFrameData::get\_program](../../debugger/debug-interface-access/idiaframedata-get-program.md) метод  `NULL`.  В противном случае строку программы содержит все сведения, необходимые для вычисления предыдущие значения регистра.  
  
## См. также  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)   
 [IDiaFrameData::get\_program](../../debugger/debug-interface-access/idiaframedata-get-program.md)
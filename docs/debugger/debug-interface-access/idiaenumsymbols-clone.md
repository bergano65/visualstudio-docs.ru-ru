---
title: "IDiaEnumSymbols::Clone | Microsoft Docs"
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
  - "IDiaEnumSymbols::Clone - метод"
ms.assetid: 5c542025-98cf-4307-901f-b9430f780cf0
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumSymbols::Clone
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.  
  
## Синтаксис  
  
```cpp#  
HRESULT Clone (   
   IDiaEnumSymbols** ppenum  
);  
```  
  
#### Параметры  
 ppenum  
 \[out\] возвращает [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md) объект, содержащий дубликат перечислителя.  Скопированы символы не только перечислитель.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## См. также  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)
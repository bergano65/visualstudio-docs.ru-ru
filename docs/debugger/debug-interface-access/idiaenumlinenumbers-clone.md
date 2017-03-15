---
title: "IDiaEnumLineNumbers::Clone | Microsoft Docs"
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
  - "IDiaEnumLineNumbers::Clone - метод"
ms.assetid: fcd2479a-8ff7-4aba-a737-06123c280d54
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaEnumLineNumbers::Clone
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Создает перечислитель с тем же состоянием перечисления, что и текущий перечислитель.  
  
## Синтаксис  
  
```cpp#  
HRESULT Clone (   
   IDiaEnumLineNumbers** ppenum  
);  
```  
  
#### Параметры  
 `ppenum`  
 \[out\] возвращает [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) объект, содержащий дубликат перечислителя.  Номер линии не скопированы только перечислитель.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## См. также  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)
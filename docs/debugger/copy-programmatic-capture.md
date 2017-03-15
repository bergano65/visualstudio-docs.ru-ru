---
title: "Copy (программный захват) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 30ec235a-0abb-44b9-8852-61bc9e67ce22
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Copy (программный захват)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Копирует содержимое активного файла журнала графики \(.vsglog\) в новый файл.  
  
## Синтаксис  
  
```cpp  
void Copy(  
  wchar_t const * szNewVSGLog  
);  
```  
  
#### Параметры  
 `szNewVSGLog`  
 Имя нового файла журнала графики.  
  
## Примечания  
 Чтобы скопировать данные графики в новый файл, должны быть уже захвачены некоторые данные графики; в противном случае ничего не происходит.
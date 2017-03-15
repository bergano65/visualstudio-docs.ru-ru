---
title: "UnInit | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# UnInit
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Завершает файл журнала графики, закрывает его и освобождает все ресурсы, которые использовались во время активной записи данных графики приложением.  
  
## Синтаксис  
  
```cpp  
void UnInit();  
```  
  
## Примечания  
 `UnInit` вызывается автоматически при удалении экземпляра класса `VsgDbg`.  Если экземпляр `VsgDbg` не записывал активно данные графики, ничего не происходит.  
  
 После вызова `UnInit` на экземпляре `VsgDbg`, новый файл журнала графики может быть создан вызовом `Init` и завершен вызовом `UnInit`.  Данное действие можно повторять сколько угодно раз, если необходимо использовать один и тот же экземпляр `VsgDbg` для создания нескольких независимых файлов журнала графики.  
  
## См. также  
 [Init](../debugger/init.md)
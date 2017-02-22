---
title: "IDiaSession::put_loadAddress | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSession::put_loadAddress - метод"
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::put_loadAddress
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Задает адрес загрузки для исполняемого файла, который соответствует символам в этом хранилище символов.  
  
## Синтаксис  
  
```cpp#  
HRESULT put_loadAddress (   
   ULONGLONG NewVal  
);  
```  
  
#### Параметры  
 `NewVal`  
 \[in\] загружает адрес для исполняемого файла.  
  
## Заметки  
 Свойства виртуального адреса символов \(VA\) вычисляются с помощью значения этого метода.  Виртуальные адреса не вычисляются если это свойство не установлено в ненулевое значение.  
  
> [!NOTE]
>  Этот метод следует вызывать при получении [IDiaSession](../../debugger/debug-interface-access/idiasession.md) объект и прежде чем начать с помощью объекта если необходимо использовать любые виртуальные свойства в символах.  
  
## См. также  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)
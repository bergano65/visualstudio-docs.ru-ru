---
title: "IDiaSession::findFileById | Microsoft Docs"
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
  - "IDiaSession::findFileById - метод"
ms.assetid: 710efe04-78b5-4f3e-a1d8-f9b069063503
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSession::findFileById
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Извлекает исходный файл идентификатором исходного файла.  
  
## Синтаксис  
  
```cpp#  
HRESULT findFileById (   
   DWORD            uniqueId,  
   IDiaSourceFile** ppResult  
);  
```  
  
#### Параметры  
 `uniqueId`  
 \[in\] задает идентификатор исходного файла.  
  
 `ppResult`  
 \[out\] возвращает [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) объект, который представляет полученный файл источника.  
  
## Возвращаемое значение  
 В случае успеха возвращает `S_OK`; в противном случае возвращает код ошибки.  
  
## Заметки  
 Идентификатор исходного файла, уникальное значение, используемое внутри к пакету SDK для доступа к интерфейсу отладки, чтобы все исходные файлы уникальным.  Этот метод обычно используется внутренне к пакету SDK для доступа к интерфейсу отладки.  
  
## См. также  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)
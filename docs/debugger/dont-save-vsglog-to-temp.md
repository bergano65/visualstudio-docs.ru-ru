---
title: "DONT_SAVE_VSGLOG_TO_TEMP | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f27ab0e6-9575-4ca0-9901-37d3e5c3a2f5
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DONT_SAVE_VSGLOG_TO_TEMP
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Определяет своим наличием, сохраняется ли файл журнала графики в каталог временных файлов пользователя.  
  
## Синтаксис  
  
```cpp  
#define DONT_SAVE_VSGLOG_TO_TEMP  
```  
  
## Значение  
 Символ препроцессора, который своим наличием или отсутствием определяет, сохраняется ли файл журнала графики в каталог временных файлов пользователя.  Если этот символ определен, то имя файла, указанное `VSG_DEFAULT_RUN_FILENAME` является относительным для текущего каталога отслеживаемого приложения или абсолютным; в противном случае имя файла, указанное `VSG_DEFAULT_RUN_FILENAME`, является относительным для каталога временных файлов пользователя и не может быть абсолютным.  
  
## Примечания  
 В зависимости от привилегий пользователя файлы журнала графики могут быть не сохранены в произвольном расположении.  Рекомендуется сохранять журналы графики в каталог временных файлов пользователя или другое известное расположение, если вы не уверены, доступно ли выбранное расположение для записи пользователем.  
  
 Чтобы предотвратить сохранение файла журнала графики в каталог временных файлов, определите `DONT_SAVE_VSGLOG_TO_TEMP` до включения `vsgcapture.h`.  
  
## Пример  
 В этом примере показано, как сохранить файл журнала графики по абсолютному пути на компьютере.  
  
```  
// Define DONT_SAVE_VSGLOG_TO_TEMP and VSG_DEFAULT_RUN_FILENAME before including vsgcapture.h  
#define DONT_SAVE_VSGLOG_TO_TEMP  
#define VSG_DEFAULT_RUN_FILENAME L"C:\\Graphics Diagnostics Captures\\default.vsglog"  
  
#include <vsgcapture.h>  
  
```  
  
## См. также  
 [VSG\_DEFAULT\_RUN\_FILENAME](../debugger/vsg-default-run-filename.md)
---
title: "Указание пути к программам командной строки средств профилирования | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7047bf18-5779-4f6e-872c-66e2fc47c969
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Указание пути к программам командной строки средств профилирования
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Путь средств профилирования командной строки [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] не добавляется в переменную среды PATH.  На 32\-разрядных компьютерах эти средства находятся в одном каталоге.  Существуют 64\- и 32\-разрядные версии средств профилирования для 64\-разрядных компьютеров.  
  
## 32\-разрядные компьютеры  
 На 32\-разрядных компьютерах каталог средств профилирования по умолчанию — *диск*\\Program Files\\Microsoft Visual Studio 11.0\\Team Tools\\Performance Tools.  
  
## 64\-разрядные компьютеры  
 На 64\-разрядных компьютерах укажите путь в соответствии с целевой платформой профилируемого приложения.  
  
-   Для 32\-разрядных приложений каталог средств профилирования по умолчанию:  
  
     *диск*\\Program Files \(x86\)\\Microsoft Visual Studio 11.0\\Team Tools\\Performance Tools  
  
-   Для 64\-разрядных приложений каталог средств профилирования по умолчанию:  
  
     *диск*\\Program Files \(x86\)\\Microsoft Visual Studio 11.0\\Team Tools\\Performance Tools\\x64
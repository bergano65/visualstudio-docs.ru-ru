---
title: "Отладка приложений ASP.NET и AJAX | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "отладка [ASP.NET], сведения об отладке ASP.NET"
  - "отладка веб-приложений ASP.NET"
  - "отладка, WCF"
  - "WCF, отладка"
ms.assetid: 9d531913-541b-47b8-864d-138021fca0c6
caps.latest.revision: 31
caps.handback.revision: 31
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Отладка приложений ASP.NET и AJAX
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Отладка веб\-приложений [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] подобна отладке приложений Windows Form или отладке любого другого приложения Windows, поскольку оба типа приложений содержат элементы управления и события.  Однако существуют основные различия между двумя типами приложений:  
  
-   Выполнять отслеживание состояния более сложно, чем в веб\-приложении.  
  
-   В приложениях Windows код для отладки в большинстве случаев расположен в одном месте. В веб\-приложениях код может быть расположен на клиенте или на сервере.  Если код [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] полностью расположен на сервере, то код JavaScript или [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] может быть расположен на клиенте.  
  
## В этом подразделе  
 [Подготовка к отладке ASP.NET](../debugger/preparing-to-debug-aspnet.md)  
 Описаны шаги, которые необходимы для включения отладки приложений [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
 [Отладка веб\-приложений](../debugger/debugging-web-applications.md)  
 Обсуждение отладки приложения [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], включая приложения скриптов с включенной технологией Ajax.  
  
## Связанные подразделы  
 [Управление исключениями с помощью отладчика](../debugger/managing-exceptions-with-the-debugger.md)  
 Объясняется, почему для отладки исключений [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] должен быть включен режим "Только мой код".  
  
 [Debugging and Tracing Ajax Applications Overview](../Topic/Debugging%20and%20Tracing%20Ajax%20Applications%20Overview.md)  
 Обсуждаются некоторые методы и средства, которые могут помочь в отладке кода AJAX.  
  
 [Использование IntelliTrace](../debugger/intellitrace.md)  
 Ускорение отладки кода за счет использования IntelliTrace для ведения и просмотра журнала состояний приложения без необходимости частого перезапуска приложения.  Возможность просматривать информацию о событиях и вызовах, произошедших во время выполнения приложения, и возможность запускать отладку, начиная с этих моментов времени.  Доступно только в Visual Studio Ultimate.  
  
## См. также  
 [Безопасность отладчика](../debugger/debugger-security.md)   
 [Отладка веб\-приложений и скриптов](../debugger/debugging-web-applications-and-script.md)   
 [Параметры отладки и подготовка](../debugger/debugger-settings-and-preparation.md)   
 [Основы отладки](../debugger/debugger-basics.md)
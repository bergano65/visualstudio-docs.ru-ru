---
title: "Ошибка: не удалось автоматически перейти в режим пошагового выполнения | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.error.causality_no_server_response"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "удаленная отладка, ошибка уведомления"
ms.assetid: 9a370ccc-d358-429c-b285-9b6c0649bc68
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Ошибка: не удалось автоматически перейти в режим пошагового выполнения
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Текст сообщения об ошибке.  
  
 "Не удается автоматически выполнить шаг на сервере. Отладчик не получил уведомления перед выполнением удаленной процедуры."  
  
 Эта ошибка может возникнуть, когда предпринята попытка в пошаговом режиме зайти в веб\-службу \(см. раздел [Вход в пошаговом режиме в веб\-службу XML](http://msdn.microsoft.com/ru-ru/8e67de38-bf5f-41cc-a457-1b88ce63d764)\). Ошибка может произойти всякий раз при неправильно настроенном [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
 Возможные причины:  
  
-   Параметр отладки не установлен в "true" в файле web.config приложения [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] \(см. раздел [Режим отладки в приложениях ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)\).  
  
-   Версия [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] была установлена после установки Visual Studio.[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] следует устанавливать до Visual Studio. Чтобы устранить эту неполадку, откройте **Панель управления** Windows и воспользуйтесь компонентом **Программы и компоненты** для исправления установки Visual Studio.  
  
## См. также  
 [Ошибки удаленной отладки и их устранение](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Удаленная отладка](../debugger/remote-debugging.md)
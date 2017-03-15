---
title: "Условия для удаленной отладки веб-приложений | Microsoft Docs"
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
  - "отладка веб-приложений ASP.NET, удаленные серверы"
  - "удаленная отладка, необходимые компоненты"
  - "удаленные серверы, отладка веб-приложений"
ms.assetid: 1cd777b5-6d20-4ca6-a0df-51653b118469
caps.latest.revision: 27
caps.handback.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Условия для удаленной отладки веб-приложений
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

С помощью отладчика [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] можно простым и понятным образом отладить веб\-приложение как на локальном компьютере, так и на удаленном сервере.  Это означает, что отладчик работает одинаково и предоставляет одни и те же возможности на любом компьютере.  Однако для правильного выполнения удаленной отладки необходимо предварительно выполнить несколько условий.  
  
-   На сервере, на котором предполагается выполнять отладку, должны быть установлены компоненты удаленной отладки [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Дополнительные сведения см. в разделе [Настройка удаленной отладки](../Topic/Set%20Up%20the%20Remote%20Tools%20on%20the%20Device.md).  
  
-   Рабочий процесс [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] по умолчанию выполняется в качестве пользовательского процесса ASPNET.  Следовательно, для отладки приложения на компьютере, на котором выполняется [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], необходимо обладать правами администратора.  Имя рабочего процесса [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] зависит от сценария отладки и версии IIS.  Дополнительные сведения см. в разделе [Практическое руководство. Поиск имени процесса ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
## См. также  
 [Отладка приложений ASP.NET и AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Требования к системе](../debugger/aspnet-debugging-system-requirements.md)
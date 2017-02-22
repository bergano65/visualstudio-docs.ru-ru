---
title: "Отладка ASP.NET: системные требования | Microsoft Docs"
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
  - "отладка веб-приложений ASP.NET, требования к системе"
  - "отладка веб-приложений ASP.NET, требования безопасности"
ms.assetid: 7810b9b2-debf-4271-8fc7-1df031123255
caps.latest.revision: 38
caps.handback.revision: 38
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Отладка ASP.NET: системные требования
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

В этом разделе описаны требования к программному обеспечению и безопасности для сценариев локальной и удаленной отладки [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
-   При локальной отладке [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] и веб\-приложение выполняются на одном и том же компьютере. Существуют две версии этого сценария:  
  
    -   код [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] располагается в файловой системе;  
  
    -   код [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] располагается на веб\-сайте служб IIS.  
  
-   При удаленной отладке [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] выполняется на клиентском компьютере и используется для отладки веб\-приложения, работающего на удаленном \(серверном\) компьютере.  
  
## Требования безопасности  
 Для удаленной отладки локальный и удаленный компьютеры должны входить в домен или рабочую группу.  
  
 Чтобы выполнить отладку рабочего процесса [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], необходимо иметь разрешение на отладку этого процесса. По умолчанию приложения [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] выполняются от имени учетной записи пользователя **ASPNET**. Если рабочий процесс выполняется от имени учетной записи **ASPNET** или **NETWORK SERVICE**, для его отладки необходимо иметь права администратора.  
  
 Имя рабочего процесса [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] варьируется в зависимости от сценария отладки и версии служб IIS. Дополнительные сведения см. в разделе [Практическое руководство. Поиск имени процесса ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md).  
  
 Вы можете изменить учетную запись пользователя, от имени которой должен выполняться рабочий процесс [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. Для этого следует внести соответствующие изменения в файл machine.config на сервере, на котором запускаются службы IIS. Оптимальный способ сделать это — с помощью **Диспетчера служб IIS**. Для получения дополнительной информации см. [Практическое руководство. Выполнение рабочего процесса с учетной записью пользователя](../debugger/how-to-run-the-worker-process-under-a-user-account.md).  
  
 Если в качестве учетной записи, от имени которой должен запускаться рабочий процесс [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], указать собственную учетную запись, то обладать правами администратора на сервере, на котором работают службы IIS, не потребуется.  
  
> [!CAUTION]
>  Прежде чем запускать рабочий процесс [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] от имени другой учетной записи, проанализируйте последствия возможной вредоносной атаки на рабочий процесс [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] при его выполнении от имени этой учетной записи. Учетные записи ASPNET и NETWORK SERVICE обладают минимальным набором разрешений, минимизируя возможный вред в случае вредоносной атаки на процесс. При выполнении рабочего процесса [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] от имени учетной записи с более широким объемом прав объем возможного вреда возрастает.  
  
## См. также  
 [Отладка приложений ASP.NET и AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Практическое руководство. Выполнение рабочего процесса с учетной записью пользователя](../debugger/how-to-run-the-worker-process-under-a-user-account.md)
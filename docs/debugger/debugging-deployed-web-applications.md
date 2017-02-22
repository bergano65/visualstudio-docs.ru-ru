---
title: "Отладка развернутых веб-приложений | Microsoft Docs"
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
  - "веб-приложения ASP.NET"
  - "ASP.NET, отладка веб-приложений"
  - "отладка веб-служб"
  - "веб-службы, отладка"
  - "веб-службы XML, отладка"
  - "XML, отладка веб-служб"
ms.assetid: b938a91b-be96-416f-83bc-4177e7f3929a
caps.latest.revision: 31
caps.handback.revision: 31
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Отладка развернутых веб-приложений
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Если необходимо выполнить отладку веб\-приложения, которое выполняется на рабочем сервере, это необходимо делать с осторожностью.  Если выполнить присоединение к рабочему процессу [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], например, для отладки и установки точки останова, весь управляемый код процесса останавливается.  Прекращение выполнения всего управляемого кода в рабочем процессе может привести к остановке работы для всех пользователей сервера.  Перед отладкой рабочего сервера примите во внимание потенциальное воздействие на рабочий сервер.  
  
 Чтобы использовать [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] для отладки развернутого приложения, необходимо выполнить присоединение к рабочему процессу [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] и убедиться в том, что отладчик имеет доступ к символам для приложения.  Кроме того, необходимо найти и открыть исходные файлы для данного приложения.  Дополнительные сведения см. в разделах [Указание файлов символов \(.pdb\) и файлов с исходным кодом](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), [Практическое руководство. Поиск имени процесса ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md) и [Требования к системе](../debugger/aspnet-debugging-system-requirements.md).  
  
> [!NOTE]
>  Во многих веб\-приложениях [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] имеются ссылки на библиотеки DLL, содержащие бизнес\-логику или другой полезный код.  Такая ссылка автоматически копирует библиотеку DLL с локального компьютера в папку \\bin виртуального каталога веб\-приложения.  При выполнении отладки помните, что веб\-приложение ссылается на данную копию библиотеки DLL, а не на копию, находящуюся на локальном компьютере.  
  
 Процесс для присоединения к рабочему процессу [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] аналогичен процессу присоединения к любым другим удаленным процессам.  После присоединения, если соответствующий проект не открыт, при остановке приложения появляется диалоговое окно.  Это диалоговое окно запрашивает расположение исходных файлов для приложения.  Имя файла, указанное в диалоговом окне, должно соответствовать имени файла, заданному в символах отладки на веб\-сервере.  Дополнительные сведения см. в разделе [Присоединение к выполняемым процессам](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
## См. также  
 [Отладка приложений ASP.NET и AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Отладка веб\-приложений и скриптов](../debugger/debugging-web-applications-and-script.md)   
 [Практическое руководство. Включение отладки для приложений ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [Практическое руководство. Поиск имени процесса ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md)   
 [Указание файлов символов \(.pdb\) и файлов с исходным кодом](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
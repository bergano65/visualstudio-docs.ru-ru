---
title: "Практическое руководство. Отладка веб-приложений | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "Веб-формы ASP.NET, отладка"
  - "ASP.NET, отладка веб-приложений"
  - "отладка веб-приложений ASP.NET, во время разработки"
  - "веб-службы, отладка"
ms.assetid: 6440d12e-6b29-42c5-a958-99aeaaff480f
caps.latest.revision: 37
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 37
---
# Практическое руководство. Отладка веб-приложений
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] – это основная технология разработки веб\-приложений в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Отладчик [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] предоставляет мощные средства для локальной отладки веб\-приложений [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] или их отладки на удаленном сервере.  В этом разделе описано, как выполнить отладку проекта [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] во время разработки.  Сведения об отладке веб\-приложения [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)], развертывание которого выполнено на рабочем сервере, см. в разделе [Отладка развернутых веб\-приложений](../debugger/debugging-deployed-web-applications.md).  
  
 Чтобы выполнить отладку приложения [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]:  
  
-   Необходимо иметь требуемые разрешения.  Дополнительные сведения см. в разделе [Требования к системе](../debugger/aspnet-debugging-system-requirements.md).  
  
-   Отладка [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] должна быть включена в окне **Свойства проекта**.  
  
-   В файле конфигурации данного приложения \(Web.config\) необходимо установить режим отладки.  В режиме отладки [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] генерирует символы для динамически сгенерированных файлов и включает присоединение отладчика к приложению [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] устанавливает это автоматически при запуске отладки, если проект создан на основе шаблона веб\-проектов.  
  
-   Дополнительные сведения см. в разделе [Практическое руководство. Включение отладки для приложений ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md).  
  
### Отладка веб\-приложения во время разработки  
  
1.  В меню **Отладка** выберите команду **Пуск**, чтобы начать отладку веб\-приложения.  
  
     С помощью [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] выполняется построение проекта веб\-приложения, развертывание \(если необходимо\), запуск сервера разработки ASP.NET при локальной отладке и присоединение к рабочему процессу [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
2.  Используйте отладчик, чтобы создавать и снимать точки останова, переходить и выполнять другие операции отладки, как и для любого другого приложения.  
  
     Дополнительные сведения см. в разделе [Основы отладки](../debugger/debugger-basics.md).  
  
3.  В меню **Отладка** щелкните команду **Остановить отладку**, чтобы остановить сеанс отладки или в меню **Файл** в Internet Explorer выполните команду **Закрыть**.  
  
## См. также  
 [Отладка веб\-приложений и скриптов](../debugger/debugging-web-applications-and-script.md)   
 [Отладка приложений ASP.NET и AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Практическое руководство. Включение отладки для приложений ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)
---
title: "Подготовка к отладке: веб-приложения ASP.NET | Microsoft Docs"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "отладка [Visual Studio], в веб-приложениях"
  - "отладка веб-приложений ASP.NET"
ms.assetid: bcfb1080-98d1-42f9-96af-186fb14f232a
caps.latest.revision: 35
caps.handback.revision: 35
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Подготовка к отладке: веб-приложения ASP.NET
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Шаблон веб\-узла [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] служит для создания приложения Web Forms.  При создании веб\-узла с помощью этого шаблона [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] задает отладочные настройки по умолчанию.  В диалоговом окне **Свойства проекта** можно указать, следует ли назначить данную веб\-страницу стартовой.  При запуске отладки веб\-узла [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] с параметрами, установленными по умолчанию, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] запустит обозреватель Internet Explorer и присоединит отладчик к рабочему процессу [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] \(aspnet\_wp.exe или w3wp.exe\).  Дополнительные сведения см. в разделе [Требования к системе](../debugger/aspnet-debugging-system-requirements.md).  
  
### Создание приложения Web Forms  
  
1.  В меню **Файл** выберите команду **Создать веб\-узел**.  
  
2.  В диалоговом окне **Создание веб\-сайта** выберите **Веб\-сайт** [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  
  
3.  Нажмите кнопку **ОК**.  
  
### Отладка форм Web Forms  
  
1.  Разместите точки останова в функциях и обработчиках событий.  
  
     Дополнительные сведения см. в разделе [Breakpoints and Tracepoints](http://msdn.microsoft.com/ru-ru/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
2.  Когда будет достигнута точка останова, выполните шаг с заходом внутрь этой функции.  Наблюдайте за выполнением кода, пока не изолируете проблему.  
  
     Дополнительные сведения см. в разделах [Stepping](http://msdn.microsoft.com/ru-ru/8791dac9-64d1-4bb9-b59e-8d59af1833f9) и [Отладка веб\-приложений и скриптов](../debugger/debugging-web-applications-and-script.md).  
  
## Изменение настроек по умолчанию  
 При желании можно изменить стандартные параметры конфигурации для отладки и конфигурации для выпуска, созданные [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Дополнительные сведения см. в разделе [Практическое руководство. Настройка конфигураций отладки и выпуска](../debugger/how-to-set-debug-and-release-configurations.md).  
  
#### Изменение используемых по умолчанию параметров конфигурации отладки  
  
1.  В области **Обозреватель решений** щелкните правой кнопкой мыши веб\-узел и выберите пункт **Страницы свойств**, чтобы вызвать диалоговое окно **Страницы свойств**.  
  
2.  Выберите **Параметры запуска**.  
  
3.  Укажите в поле **Действие при запуске** веб\-страницу, которая должна отображаться первой.  
  
4.  Убедитесь, что в разделе **Отладчики** выбран пункт **Отладка ASP.NET**.  
  
     Дополнительные сведения см. в разделе [Параметры страниц свойств для веб\-проектов](../debugger/property-pages-settings-for-web-projects.md).  
  
## См. также  
 [Параметры отладки и подготовка](../debugger/debugger-settings-and-preparation.md)   
 [Основы отладки](../debugger/debugger-basics.md)   
 [Безопасность отладчика](../debugger/debugger-security.md)   
 [Отладка управляемого кода](../debugger/debugging-managed-code.md)
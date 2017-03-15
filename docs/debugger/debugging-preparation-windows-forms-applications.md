---
title: "Подготовка к отладке: приложения Windows Forms | Microsoft Docs"
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
  - "отладка [C#], приложения Windows"
  - "отладка [J#], приложения Windows"
  - "отладка [Visual Basic], приложения Windows"
  - "отладка [Visual Studio], приложения Windows"
  - "отладка приложений Windows"
  - "приложения Windows, отладка"
ms.assetid: 7092ee7f-8378-4def-aef8-1695bd97cf14
caps.latest.revision: 28
caps.handback.revision: 28
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Подготовка к отладке: приложения Windows Forms
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Шаблон проекта Windows Forms создает приложение Windows Forms.  Отладка приложений такого типа в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] не вызывает никаких затруднений.  Дополнительные сведения см. в разделе [Creating a Windows Application Project](http://msdn.microsoft.com/ru-ru/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
 При создании проекта Windows Forms из шаблона проекта, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] автоматически создает требуемые параметры для отладки и выпуска.  При необходимости эти параметры можно изменить.  Эти параметры могут быть изменены в диалоговом окне **Страницы свойств \<имя проекта\>** \(**Мой проект** в Visual Basic\).  
  
 Дополнительные сведения см. в разделе [Рекомендуемые параметры свойств](../debugger/managed-debugging-recommended-property-settings.md).  
  
 В следующей таблице приведены дополнительные параметры, рекомендуемые к использованию.  
  
### "Свойства конфигурации" во вкладке "Отладка"  
  
|**Имя свойства**|**Параметр**|  
|----------------------|------------------|  
|**Действие при запуске**|-   Установите в **Запуск проекта** в большинстве случаев.  Установите в **Запуск внешней программы**, если требуется запускать другой исполняемый файл при запуске отладки \(обычно для отладки DLL\).|  
  
 Можно выполнять отладку приложений Windows Forms из [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] или путем присоединения к уже запущенному приложению.  Дополнительные сведения о присоединении см. в разделе [Присоединение к выполняемым процессам](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
### Выполнение отладки приложения Windows Forms на C\#, F\# или Visual Basic  
  
1.  Откройте проект в [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
2.  Создайте точки останова, если требуется.  
  
     Поскольку приложения Windows Forms управляются событиями, точки останова появятся в коде обработчиков событий, или в методах, вызываемых ими.  Типичные события, в которые стоит помещать точки останова:  
  
    1.  события, связанные с элементом управления, такие как Click, Enter, и т.д.;  
  
    2.  события, связанные с запуском приложений и завершением работы, такие как Load, Activated и т. д.;  
  
    3.  события, связанные с фокусом и проверками.  
  
     Дополнительные сведения см. в разделе [Creating Event Handlers in Windows Forms](../Topic/Creating%20Event%20Handlers%20in%20Windows%20Forms.md).  
  
3.  В меню **Отладка** выберите команду **Запуск**.  
  
4.  Отладка использует методы, обсуждаемые в [Основы отладки](../debugger/debugger-basics.md).  
  
## См. также  
 [Отладка управляемого кода](../debugger/debugging-managed-code.md)   
 [Типы проектов C\#, F\# и Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Практическое руководство. Настройка конфигураций отладки и выпуска](../debugger/how-to-set-debug-and-release-configurations.md)   
 [Параметры проекта для конфигураций отладки C\#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Параметры проекта для конфигурации отладки Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Присоединение к выполняемым процессам](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Windows Forms](../Topic/Windows%20Forms.md)
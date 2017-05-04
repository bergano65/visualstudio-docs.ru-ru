---
title: "Построение и отладка решений SharePoint | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "разработка приложений SharePoint в Visual Studio, построение и отладка"
  - "разработка приложений SharePoint в Visual Studio, отладка"
ms.assetid: c9e7c9ab-4eb3-40cd-a9b9-6c2a896f70ae
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Построение и отладка решений SharePoint
  В общем, построение и отладка решений SharePoint аналогичны созданию и отладке других типов проектов в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  В этом разделе описываются существующие различия.  
  
## Выходные данные проекта для решений SharePoint  
 При построении решений SharePoint создаются сборки и пакет решения \(WSP\-файл\).  В следующей таблице приведено расположение этих файлов во время выполнения построения.  
  
|Элемент построения|Выходная папка|  
|------------------------|--------------------|  
|Сборка, база данных программы \(PDB\) и WPS\-файлы.|*ProjectName*\\bin\\debug или *ProjectName*\\bin\\release|  
|Файлы элементов проекта SharePoint.|*ProjectName*\\package\\debug или *ProjectName*\\package\\release|  
|Построение промежуточных файлов.|*ProjectName*\\obj\\debug или *ProjectName*\\obj\\release|  
|Упаковка промежуточных файлов.|*ProjectName*\\pkgobj\\debug или *ProjectName*\\pkgobj\\release|  
  
## Построение решений SharePoint  
 Для построения решений SharePoint на компьютере разработчика должна быть установлена правильная версия сервера SharePoint.  В противном случае, построение решений SharePoint аналогично построению других типов проектов в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Для получения дополнительной информации см. [Практическое руководство. Построение решений SharePoint](../sharepoint/how-to-build-sharepoint-solutions.md).  
  
## Отладка и тестирование решений SharePoint  
 Перед отладкой, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] копирует пакет .wsp на сервер SharePoint, активирует сайт и веб\-компоненты, а в некоторых случаях, запускает проект.  В других случаях может понадобиться открыть проект вручную.  Дополнительные сведения см. в разделах [Устранение неполадок решений SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md) и [Отладка решений SharePoint](../sharepoint/debugging-sharepoint-solutions.md).  
  
## Проверка и отладка кода SharePoint с помощью функций управления жизненным циклом приложений  
 Функции управления жизненным циклом приложения в Visual Studio, например модульное тестирование и IntelliTrace, позволяют точнее найти проблемы в решениях SharePoint.  Профилирование позволяет найти и определить области с проблемами производительности в решениях SharePoint.  Дополнительные сведения см. в разделах [Проверка и отладка кода SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md) и [Профилирование производительности приложений SharePoint](../sharepoint/profiling-the-performance-of-sharepoint-applications.md).  
  
## Обеспечение безопасности во время построения  
 Чтобы упаковать или развернуть решения SharePoint, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] необходимо иметь разрешение на копирование файлов на сервер SharePoint.  Необходимо запустить [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] как процесс с особыми разрешениями под учетной записью "Администратор семейства сайтов" на сервере SharePoint.  Дополнительно, необходимо указать, является ли проект обезвреженным решением или решением фермы.  Для получения дополнительной информации см. [Различия между изолированными решениями и решениями фермы](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).  
  
## Использование команды очистки  
 После установки решения SharePoint на сервере SharePoint для отладки, команда **Очистить** не удалит решение.  Вместо этого, необходимо деактивировать компоненты с помощью настроек SharePoint.  
  
## См. также  
 [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)   
 [Просмотр подключений SharePoint с помощью обозревателя серверов](../sharepoint/browsing-sharepoint-connections-using-server-explorer.md)   
 [Упаковка и развертывание решений SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  
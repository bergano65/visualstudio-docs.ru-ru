---
title: "Практическое руководство. Развертывание и публикация решения SharePoint на локальном сайте SharePoint | Microsoft Docs"
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
  - "развертывание [разработка приложений SharePoint в Visual Studio]"
  - "разработка приложений SharePoint в Visual Studio, развертывание"
ms.assetid: 73f8d6a9-4c64-4bba-ae0e-9474baf8df26
caps.latest.revision: 18
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# Практическое руководство. Развертывание и публикация решения SharePoint на локальном сайте SharePoint
  Решения SharePoint можно развертывать или публиковать на локальном сервере SharePoint на компьютере разработчика.  В процессе развертывания происходит копирование WSP\-файлов на сервер, установка решения SharePoint и активация компонентов.  Процесс публикации только копирует wsp\-файл на сервер SharePoint и устанавливает его.  Необходимо вручную активировать его, чтобы использовать в SharePoint.  
  
## Развертывание решения SharePoint на локальном сервере SharePoint  
  
1.  В **обозревателе решений** выберите проект, который требуется развернуть.  
  
2.  В строке меню последовательно выберите **Сборка** и **Развернуть решение**.  
  
     WSP\-файл создается и устанавливается на локальном сервере SharePoint.  Кроме того, активируются компоненты.  
  
## Публикация решения SharePoint на локальном сервере SharePoint  
  
1.  В **Обозревателе решений** откройте контекстное меню для проекта SharePoint, который требуется опубликовать, и выберите **Опубликовать**.  
  
2.  В диалоговом окне **Опубликовать** выберите переключатель **Опубликовать в файловой системе**.  
  
3.  В текстовом поле **Целевое расположение** введите локальный путь, а затем нажмите кнопку **Опубликовать**.  
  
     Ход выполнения публикации отображается в окне **Вывода** Visual Studio.  После завершения процесса, файл решения \(.wsp\-файл\) устанавливается на локальном сервере SharePoint.  Однако его по\-прежнему необходимо активировать, чтобы использовать в SharePoint.  Если файл решения уже существует, возникает ошибка с запросом на перезапись существующего файла.  Дополнительные сведения об обновлении пакета см. в разделе об обновлении удаленных пакетов в [Практическое руководство. Развертывание, публикация и обновление решений SharePoint на удаленном сервере](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
## См. также  
 [Практическое руководство. Развертывание, публикация и обновление решений SharePoint на удаленном сервере](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md)   
 [Создание пакетов решений SharePoint](../sharepoint/creating-sharepoint-solution-packages.md)   
 [Практическое руководство. Настройка пакета решения SharePoint](../sharepoint/how-to-customize-a-sharepoint-solution-package.md)   
 [Практическое руководство. Добавление и удаление компонентов и элементов в пакете с помощью конструктора пакетов](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-package-designer.md)  
  
  
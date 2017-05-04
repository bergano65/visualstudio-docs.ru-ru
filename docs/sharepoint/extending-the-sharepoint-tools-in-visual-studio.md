---
title: "Extending the SharePoint Tools in Visual Studio | Microsoft Docs"
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
helpviewer_keywords: 
  - "Visual Studio, extending tools"
  - "extensibility [SharePoint development in Visual Studio]"
  - "SharePoint development in Visual Studio, extending tools"
ms.assetid: 084cf4bf-aaba-4277-8032-448f2cb2a124
caps.latest.revision: 39
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 38
---
# Extending the SharePoint Tools in Visual Studio
  Инструментов SharePoint в Visual Studio соответствуют требованиям многих сценариях разработки приложений.  Однако бывают ситуации, в которых их функциональности оказывается недостаточно для решения задач, которые стоят перед разработчиками.  В этих случаях можно расширить средства SharePoint, чтобы создать необходимые функции.  
  
## Расширение средств SharePoint  
 Можно раскрыть систему проекта SharePoint и узел **Подключения SharePoint** в окне **Обозреватель серверов**.  
  
### Расширение системы проектов SharePoint  
 Visual Studio включает набор шаблонов и шаблонов элементов проекта, которые можно использовать для создания решений SharePoint.  Например, имеются шаблоны для приемников событий, определений списков, рабочих процессов и веб\-частей.  Можно также определить собственные типа элементов проекта SharePoint для создания таких компонентов SharePoint как поля и настраиваемые действия.  Также можно создать расширения для типов элементов проекта SharePoint, поставляемых с Visual Studio; также можно создавать расширения для проектов SharePoint.  
  
 Дополнительные сведения см. в разделе [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md).  
  
### Расширение узла подключений SharePoint в обозревателе серверов  
 В Visual Studio можно использовать узел**Подключения SharePoint** в окне**Обозреватель серверов** для просмотра многие компоненты одного или нескольких локальных сайтов SharePoint, в иерархическом представлении в виде дерева. Можно также расширить узел **Подключения SharePoint** следующими способами:  
  
-   путем добавления собственных узлов.  Это бывает удобно, если требуется отображать компоненты сайтов SharePoint, которые не отображаются по умолчанию;  
  
-   путем расширения имеющихся узлов.  Например, можно добавить новый дочерний узел в существующий узел или добавить в узел пункт контекстного меню и выполнять задачи при нажатии разработчиком пункта меню.  
  
 Дополнительные сведения см. в разделе [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).  
  
## Требования к компьютеру разработчика  
 Для создания расширений для средств SharePoint компьютер разработчика должен соответствовать один и тот же для создания решений SharePoint в Visual Studio.  Дополнительные сведения см. в разделе [Требования по разработке решений SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md);  
  
 Также рекомендуется установить [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)].  Пакет SDK включает шаблоны проектов и средства, позволяющие расширять Visual Studio.  В частности пакет SDK включает шаблон проекта, который можно использовать для быстрого создания пакетов расширений Visual Studio \(VSIX\).  Пакеты VSIX предпочтительный способ развертывания расширений Visual Studio в Visual Studio.  Все расширения средств SharePoint необходимо развертывать с помощью пакетов VSIX.  Во всех приведенных в данных документах пошаговых руководствах предполагается, что установлен выпуск [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)].  
  
 Чтобы загрузить пакет SDK, посетите веб\-сайт [http:\/\/go.microsoft.com\/fwlink\/?LinkId\=164562](http://go.microsoft.com/fwlink/?LinkId=164562).  Дополнительные сведения о расширениях Visual Studio см. в разделе [Разработка расширений Visual Studio](../Topic/Developing%20Visual%20Studio%20Extensions.md).  
  
## См. также  
 [Overview of the Programming Model of SharePoint Tools Extensions](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)   
 [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md)   
 [Extending the SharePoint Connections Node in Server Explorer](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)   
 [Programming Concepts and Features for SharePoint Tools Extensions](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)   
 [Reference &#40;SharePoint Tools Extensibility&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)   
 [Debugging Extensions for the SharePoint Tools in Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)   
 [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  
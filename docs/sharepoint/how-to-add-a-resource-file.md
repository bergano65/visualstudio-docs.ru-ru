---
title: "Практическое руководство. Добавление файла ресурсов"
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
  - "файлы ресурсов [разработка приложений SharePoint в Visual Studio]"
  - "разработка приложений SharePoint в Visual Studio, файлы ресурсов"
ms.assetid: 2b4ac232-992e-4070-8e98-6f11eb88e1a8
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Практическое руководство. Добавление файла ресурсов
  Команды для добавления файлов ресурсов можно найти в контекстном меню узла решения и узлов компонентов в обозревателе решений.  Для получения дополнительной информации см. [Локализация решений SharePoint](../sharepoint/localizing-sharepoint-solutions.md).  
  
### Добавление глобального файла ресурсов в решение SharePoint  
  
1.  В [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] откройте решение SharePoint.  
  
2.  В области **Обозреватель решений** выберите узел проекта SharePoint, затем в меню **Проект** выберите **Добавить новый элемент**.  
  
3.  В диалоговом окне **Добавление нового элемента** выберите шаблон **Глобальный файл ресурсов** и нажмите кнопку **Добавить**.  
  
    > [!NOTE]  
    >  Шаблон элемента проекта "Глобальный файл ресурсов" появляется только при выборе элемента проекта SharePoint.  
  
4.  В диалоговом окне **Добавление ресурса** выберите язык файла ресурсов, например "Английский \(США\)".  
  
     Это действие добавит в решение глобальный файл ресурсов с именем вида Resource*x***.***culture***.**resx, например: Resource1.en\-US.resx.  
  
5.  Когда **Редактор ресурсов** будет открыт в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] добавьте ресурсы в файл ресурсов.  
  
### Добавление файла ресурсов компонента SharePoint  
  
1.  Если решение SharePoint еще не открыто в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], откройте решение.  
  
2.  В **обозревателе решений** откройте контекстное меню имени компонента в узле **Компоненты** и выберите пункт **Добавить ресурс компонента**.  
  
     Это действие добавит файл ресурсов в компонент в формате *ResourceFileName***.***culture***.**resx, например, Feature1.en\-US.resx.  
  
3.  Когда **Редактор ресурсов** будет открыт в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] добавьте ресурсы в файл ресурсов.  
  
## См. также  
 [Разработка решений SharePoint](../sharepoint/developing-sharepoint-solutions.md)  
  
  
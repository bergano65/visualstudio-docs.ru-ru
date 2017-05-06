---
title: "Практическое руководство. Добавление кнопки запуска диалогового окна в группу ленты"
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
  - "кнопка вызова диалогового окна [разработка решений Office в Visual Studio]"
  - "лента [разработка решений Office в Visual Studio], кнопка вызова диалогового окна"
ms.assetid: 5972664f-4e37-4dc6-90d0-69cedd057e60
caps.latest.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 18
---
# Практическое руководство. Добавление кнопки запуска диалогового окна в группу ленты
  В любую группу ленты можно добавить кнопку запуска диалогового окна.  Кнопка вызова диалогового окна ленты представляет собой небольшой значок, отображаемый в группе.  Пользователь нажимает эту кнопку для открытия связанных диалоговых окон или панелей задач, которые предоставляют дополнительные параметры, связанные с данной группой.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### Добавление кнопки запуска диалогового окна в группу ленты  
  
1.  Выберите файл кода ленты \(с расширением VB или CS\) в **Обозревателе решений**.  
  
2.  В меню **Вид** выберите **Конструктор**.  
  
3.  В конструкторе лент щелкните правой кнопкой мыши любую группу и выберите команду **Добавить кнопку вызова диалогового окна**.  
  
     Добавьте код в обработчик событий <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick> группы для открытия пользовательского или встроенного диалогового окна.  
  
## См. также  
 [Обзор ленты](../vsto/ribbon-overview.md)   
 [Доступ к ленте во время выполнения](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Образцы и пошаговые руководства разработки Office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Конструктор лент](../vsto/ribbon-designer.md)   
 [Общие сведения об объектной модели ленты](../vsto/ribbon-object-model-overview.md)   
 [XML-ленты](../vsto/ribbon-xml.md)   
 [Практическое руководство. Экспорт лент из конструктора лент в XML-ленты](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)   
 [Практическое руководство. Изменение положения вкладки на ленте](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)   
 [Практическое руководство. Настройка встроенной вкладки](../vsto/how-to-customize-a-built-in-tab.md)   
 [Практическое руководство. Добавление элементов управления в представление Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)   
 [Настройка ленты для Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Практическое руководство. Работа с настройкой ленты](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Практическое руководство. Просмотр ошибок пользовательского интерфейса надстройки](../vsto/how-to-show-add-in-user-interface-errors.md)   
 [Пошаговое руководство. Создание настраиваемой вкладки с помощью конструктора лент](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Пошаговое руководство. Обновление элементов управления на ленте во время выполнения](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Пошаговое руководство. Создание настраиваемой вкладки с помощью XML-лент](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  
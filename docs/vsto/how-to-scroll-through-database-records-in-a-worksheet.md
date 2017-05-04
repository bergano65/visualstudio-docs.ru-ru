---
title: "Практическое руководство. Прокрутка записей базы данных на листе | Microsoft Docs"
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
  - "данные [разработка решений Office в Visual Studio], прокрутка записей базы данных"
  - "базы данных [разработка решений Office в Visual Studio], прокрутка записей"
  - "записи [разработка решений Office в Visual Studio], прокрутка"
  - "листы [разработка решений Office в Visual Studio], прокрутка записей"
ms.assetid: aea4c86c-9d6d-47dd-8977-066e21945dab
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# Практическое руководство. Прокрутка записей базы данных на листе
  Следующая процедура поясняет, как с помощью конструктора отобразить на листе Microsoft Office Excel одно поле из таблицы базы данных, используя элементы управления, позволяющие конечному пользователю просматривать все записи в базе данных.  
  
 Конструктор можно использовать только в проектах уровня документа.  Добавление элементов управления и их программная привязка к данным может также выполняться во время выполнения.  Дополнительные сведения см. в разделе [Пошаговое руководство. Простая привязка данных в проекте надстройки VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
### Чтобы прокрутить записи базы данных на листе, выполните следующие действия:  
  
1.  Откройте в Visual Studio проект приложения Excel.  
  
2.  Откройте окно **Источники данных** и создайте из базы данных источник данных.  Дополнительные сведения см. в разделе [Практическое руководство. Подключение к данным в базе данных](../Topic/How%20to:%20Connect%20to%20Data%20in%20a%20Database.md).  
  
3.  Разверните таблицу, содержащую данные, которые требуется отобразить, и выберите нужный столбец.  
  
4.  Откройте список элементов управления и выберите **NamedRange**.  
  
5.  Перетащите элемент управления <xref:Microsoft.Office.Tools.Excel.NamedRange> на ячейку, в которой должны находиться данные.  
  
6.  На вкладке **Windows Forms** окна **Панель элементов** добавьте на лист элемент управления <xref:System.Windows.Forms.BindingNavigator> и настройте элементы управления, которые необходимо использовать.  Дополнительные сведения см. в разделе [Общие сведения об элементе управления BindingNavigator &#40;Windows Forms&#41;](../Topic/BindingNavigator%20Control%20Overview%20(Windows%20Forms).md).  
  
## См. также  
 [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  
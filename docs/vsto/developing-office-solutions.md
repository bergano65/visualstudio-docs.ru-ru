---
title: "Разработка решений Office | Microsoft Docs"
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
  - "разработка решений Office в Visual Studio], сведения о разработке решений"
  - "решения [разработка решений Office в Visual Studio], разработка"
  - "решения Office [разработка решений Office в Visual Studio], разработка"
ms.assetid: 7361cfe0-dee4-48d7-a066-232f87f093ca
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 30
---
# Разработка решений Office
  После разработки проекта с помощью Office Developer Tools в Visual Studio и настройки файлов проекта можно начать реализовывать код и пользовательский интерфейс.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Модель программирования решений Office  
 Объектная модель Office предоставляет широкий набор объектов, которые можно использовать. При программировании решений Office с помощью управляемого кода вы создаете код, который использует типы в основных сборках взаимодействия Office. В решениях, создаваемых с помощью шаблонов проектов Office в Visual Studio, также можно разрабатывать код непосредственно для созданных классов в своем проекте. Для получения дополнительной информации см. [Написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md).  
  
## Программирование различных типов решений Office  
 Тип создаваемого решения определяет, какие функции можно использовать в проекте. Например, элементы управления Windows Forms и расширенные элементы управления Office \(которые называются *элементы управления ведущего приложения*\) можно добавлять в настройки на уровне документа путем перетаскивания элементов из **панели элементов** в Visual Studio во время разработки. Однако при разработке надстройки VSTO можно только добавлять эти элементы управления в документы во время выполнения путем написания кода.  
  
 Дополнительные сведения о функциях, характерных для различных типов решений, см. в следующих статьях:  
  
-   [Приступая к программированию надстроек VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   [Настройки программирования уровня документа](../vsto/programming-document-level-customizations.md).  
  
-   [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md).  
  
 Дополнительные сведения о планировании создания решений Office и процедурах создания проектов см. в статье [Проектирование и создание решений Office](../vsto/designing-and-creating-office-solutions.md).  
  
## Связанные разделы  
  
|Заголовок|Описание|  
|---------------|--------------|  
|[Написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md)|Описание различных аспектов написания кода в решениях Office.|  
|[Приступая к программированию надстроек VSTO](../vsto/programming-vsto-add-ins.md)|Общие сведения о модели программирования надстроек VSTO и связанных задачах программирования.|  
|[Настройки программирования уровня документа](../vsto/programming-document-level-customizations.md)|Общие сведения о модели программирования настроек на уровне документа и связанных задачах программирования.|  
|[Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)|Описание различных способов настройки пользовательского интерфейса приложений Office с помощью надстроек VSTO и настроек на уровне документа.|  
|[Данные в решениях Office](../vsto/data-in-office-solutions.md)|Описание различных способов работы с данными в решениях Office, например, привязки данных к элементам управления и кэширования данных в настройках на уровне документа.|  
|[Устранение неполадок при работе с решениями Office](../vsto/troubleshooting-office-solutions.md)|Советы по решению типичных проблем, которые могут происходить при создании решений Office.|  
|[Поддержка потока в Office](../vsto/threading-support-in-office.md)|Общие сведения о работе с несколькими потоками в решениях Office.|  
|[Специальные возможности в проектах Office](../vsto/accessibility-in-office-projects.md)|Описание специальных возможностей, доступных в решениях Office.|  
  
## См. также  
 [Практическое руководство. Создание и изменение настраиваемых свойств документа](../vsto/how-to-create-and-modify-custom-document-properties.md)   
 [Практическое руководство. Чтение и запись в свойства документа](../vsto/how-to-read-from-and-write-to-document-properties.md)   
 [Практическое руководство. Назначение многоязыкового пользовательского интерфейса Office](../vsto/how-to-target-the-office-multilingual-user-interface.md)   
 [Пошаговое руководство. Создание первой надстройки VSTO для Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)   
 [Пошаговое руководство. Создание первой настройки уровня документа для Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [Пошаговое руководство. Создание первой надстройки VSTO для Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)   
 [Пошаговое руководство. Создание первой надстройки VSTO для PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [Пошаговое руководство. Создание первой надстройки VSTO для Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [Пошаговое руководство. Создание первой надстройки VSTO для Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)   
 [Пошаговое руководство. Создание первой настройки уровня документа для Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)  
  
  
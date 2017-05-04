---
title: "Общие задачи программирования Office | Microsoft Docs"
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
  - "разработка решений Office в Visual Studio, начало работы"
  - "часто задаваемые вопросы [разработка решений Office в Visual Studio]"
  - "разработка решений Office в Visual Studio, часто задаваемые вопросы"
ms.assetid: 7afc9bad-1d31-486e-beea-91e6d308cd67
caps.latest.revision: 45
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# Общие задачи программирования Office
  Этот раздел призван помочь вам найти ответы на следующие категории часто задаваемых вопросов о программировании решений Office с помощью Visual Studio:  
  
-   [Установка и общие задачи](#projects)  
  
-   [Задачи по настройке пользовательского интерфейса](#ui)  
  
-   [Задачи автоматизации Excel](#excel)  
  
-   [Задачи автоматизации Word](#word)  
  
-   [Задачи работы с данными](#data)  
  
-   [Задачи управления документами на стороне сервера](#server)  
  
-   [Задачи по обеспечению безопасности](#security)  
  
-   [Задачи развертывания](#deployment)  
  
##  <a name="projects"></a> Установка и общие задачи  
  
-   [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
-   [Практическое руководство. Обновление решений Office](http://msdn.microsoft.com/ru-ru/a269e539-b717-4680-a568-2152b070347e)  
  
-   [Практическое руководство. Установка основных сборок взаимодействия Microsoft Office](../vsto/how-to-install-office-primary-interop-assemblies.md).  
  
-   [Практическое руководство. Обращение к приложениям Office с помощью основных сборок взаимодействия](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md).  
  
-   [Практическое руководство. Создание обработчиков событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
-   [Практическое руководство. Открытие решений Office без выполнения кода](../vsto/how-to-open-office-solutions-without-running-code.md).  
  
-   [Практическое руководство. Установка сведений о конфигурации для решений Office](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md).  
  
-   [Практическое руководство. Отображение вкладки разработчика на ленте](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
-   [Практическое руководство. Просмотр ошибок пользовательского интерфейса надстройки](../vsto/how-to-show-add-in-user-interface-errors.md).  
  
##  <a name="ui"></a> Задачи по настройке пользовательского интерфейса  
  
### Элементы управления в документах и на листах  
  
-   [Практическое руководство. Добавление элементов управления Windows Forms в документы Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).  
  
-   [Практическое руководство. Добавление элементов управления NamedRange на листы](../vsto/how-to-add-namedrange-controls-to-worksheets.md).  
  
-   [Практическое руководство. Добавление элементов управления ListObject на листы](../vsto/how-to-add-listobject-controls-to-worksheets.md).  
  
-   [Практическое руководство. Добавление элементов управления Windows Forms в документы Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).  
  
-   [Практическое руководство. Добавление элементов управления содержимым в документы Word](../vsto/how-to-add-content-controls-to-word-documents.md).  
  
-   [Практическое руководство. Добавление закладок в документы Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md).  
  
### Области задач в настройках уровня документа  
  
-   [Практическое руководство. Добавление области действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  
  
### Области задач в надстройках VSTO  
  
-   [Практическое руководство. Добавление настраиваемой панели задач в приложение](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).  
  
### Настройки ленты  
  
-   [Практическое руководство. Работа с настройкой ленты](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
-   [Практическое руководство. Изменение положения вкладки на ленте](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md).  
  
-   [Практическое руководство. Настройка встроенной вкладки](../vsto/how-to-customize-a-built-in-tab.md).  
  
-   [Практическое руководство. Добавление элементов управления в представление Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md).  
  
-   [Практическое руководство. Экспорт лент из конструктора лент в XML-ленты](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).  
  
### Области формы Outlook  
  
-   [Практическое руководство. Добавление области формы в проект надстройки Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
-   [Практическое руководство. Отсутствие отображения области формы в Outlook](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md).  
  
### Настраиваемые меню  
  
-   [Практическое руководство. Добавление команд в контекстное меню](../vsto/how-to-add-commands-to-shortcut-menus.md).  
  
##  <a name="excel"></a> Задачи автоматизации Excel  
  
-   [Практическое руководство. Программное отображение строки в ячейке листа](../vsto/how-to-programmatically-display-a-string-in-a-worksheet-cell.md).  
  
-   [Практическое руководство. Программное создание книг Excel](../vsto/how-to-programmatically-create-new-workbooks.md).  
  
-   [Практическое руководство. Программное открытие книг Excel](../vsto/how-to-programmatically-open-workbooks.md).  
  
-   [Практическое руководство. Программное сохранение книг Excel](../vsto/how-to-programmatically-save-workbooks.md).  
  
-   [Практическое руководство. Программное закрытие книг Excel](../vsto/how-to-programmatically-close-workbooks.md).  
  
-   [Практическое руководство. Программное добавление новых листов в книги Excel](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md).  
  
-   [Практическое руководство. Программное скрытие листов Excel](../vsto/how-to-programmatically-hide-worksheets.md).  
  
-   [Практическое руководство. Программное перемещение листов в книгах](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md).  
  
-   [Практическое руководство. Программная защита книг Excel](../vsto/how-to-programmatically-protect-workbooks.md).  
  
-   [Практическое руководство. Ссылки на диапазоны листов в коде программными средствами](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md).  
  
-   [Практическое руководство. Программное применение стилей к диапазонам в книгах](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md).  
  
-   [Практическое руководство. Программное изменение форматирования в строках листа, содержащих выбранные ячейки](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md).  
  
-   [Практическое руководство. Программный поиск текста в диапазонах ячеек на листе](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md).  
  
-   [Практическое руководство. Программная печать листов Excel](../vsto/how-to-programmatically-print-worksheets.md).  
  
-   [Практическое руководство. Программное выполнение вычислений Excel](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md).  
  
-   [Практическое руководство. Программная сортировка данных на листах](../vsto/how-to-programmatically-sort-data-in-worksheets.md).  
  
##  <a name="word"></a> Задачи автоматизации Word  
  
-   [Практическое руководство. Программное создание документов](../vsto/how-to-programmatically-create-new-documents.md).  
  
-   [Практическое руководство. Программное открытие существующих документов](../vsto/how-to-programmatically-open-existing-documents.md).  
  
-   [Практическое руководство. Программное сохранение документов](../vsto/how-to-programmatically-save-documents.md).  
  
-   [Практическое руководство. Программное закрытие документов](../vsto/how-to-programmatically-close-documents.md).  
  
-   [Практическое руководство. Программная вставка текста в документы Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md).  
  
-   [Практическое руководство. Программное определение и выделение диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md).  
  
-   [Практическое руководство. Программный сброс диапазонов в документах Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md).  
  
-   [Практическое руководство. Программное форматирование текста в документах](../vsto/how-to-programmatically-format-text-in-documents.md).  
  
-   [Практическое руководство. Добавление элементов управления XMLNode в документы Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md).  
  
-   [Практическое руководство. Программное обновление текста закладки](../vsto/how-to-programmatically-update-bookmark-text.md).  
  
-   [Практическое руководство. Программный поиск и замена текста в документах](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md).  
  
-   [Практическое руководство. Программная печать документов](../vsto/how-to-programmatically-print-documents.md).  
  
-   [Практическое руководство. Программное таблиц в Word](../vsto/how-to-programmatically-create-word-tables.md).  
  
-   [Практическое руководство. Программное добавление строк и столбцов в таблицы Word](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md).  
  
-   [Практическое руководство. Программный подсчет символов в документах](../vsto/how-to-programmatically-count-characters-in-documents.md).  
  
##  <a name="data"></a> Задачи работы с данными  
  
### Элементы управления с привязкой к данным  
  
-   [Практическое руководство. Заполнение листов данными из базы данных](../vsto/how-to-populate-worksheets-with-data-from-a-database.md).  
  
-   [Практическое руководство. Заполнение документов данными из базы данных](../vsto/how-to-populate-documents-with-data-from-a-database.md).  
  
-   [Практическое руководство. Заполнение документов данными из служб](../vsto/how-to-populate-documents-with-data-from-services.md).  
  
-   [Практическое руководство. Заполнение документов данными из объектов](../vsto/how-to-populate-documents-with-data-from-objects.md).  
  
-   [Практическое руководство. Заполнение документов данными из базы данных](../vsto/how-to-populate-documents-with-data-from-a-database.md).  
  
-   [Практическое руководство. Заполнение документов данными из служб](../vsto/how-to-populate-documents-with-data-from-services.md).  
  
-   [Практическое руководство. Обновление источника данных с помощью данных из элемента управления ведущего приложения](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).  
  
### Кэшированные данные в решениях на уровне документа  
  
-   [Практическое руководство. Кэширование данных для автономного использования или для использования на сервере](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   [Практическое руководство. Программное кэширование источника данных в документе MS Office.](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).  
  
-   [Практическое руководство. Кэширование данных в документе, защищенном паролем](../vsto/how-to-cache-data-in-a-password-protected-document.md).  
  
### Пользовательские данные XML  
  
-   [Практическое руководство. Добавление пользовательских XML-частей в настройках уровня документа](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md).  
  
-   [Практическое руководство. Добавление пользовательских XML-частей в документы с помощью надстроек VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md).  
  
##  <a name="server"></a> Задачи управления документами на стороне сервера  
  
-   [Практическое руководство. Удаление расширений управляемого кода из документов](../vsto/how-to-remove-managed-code-extensions-from-documents.md).  
  
-   [Практическое руководство. Вложение расширений управляемого кода в документы](../vsto/how-to-attach-managed-code-extensions-to-documents.md).  
  
##  <a name="security"></a> Задачи по обеспечению безопасности  
  
-   [Практическое руководство. Подписывание решений Office](../vsto/how-to-sign-office-solutions.md).  
  
##  <a name="deployment"></a> Задачи развертывания  
  
-   [Практическое руководство. Публикация решения Office с помощью ClickOnce](http://msdn.microsoft.com/ru-ru/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)  
  
-   [Практическое руководство. Публикация решения Office уровня документа на сервере SharePoint с помощью ClickOnce](http://msdn.microsoft.com/ru-ru/2408e809-fb78-42a1-9152-00afa1522e58)  
  
-   [Практическое руководство. Установка решения Office ClickOnce](http://msdn.microsoft.com/ru-ru/14702f48-9161-4190-994c-78211fe18065)  
  
-   [Практическое руководство. Установка необходимых компонентов на компьютерах конечных пользователей для запуска решений Office](http://msdn.microsoft.com/ru-ru/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98)  
  
-   [Практическое руководство. Подготовка служб IIS для развертывания решений Office](http://msdn.microsoft.com/ru-ru/f62bce70-81d4-4f8b-86e6-2f2afec5d9b4)  
  
-   [Практическое руководство. Обновление развернутых решений Office](http://msdn.microsoft.com/ru-ru/be96db53-b6ea-46ab-b8d9-b76b098b3b13)  
  
-   [Практическое руководство. Изменение пути установки решения Office](http://msdn.microsoft.com/ru-ru/d0eaa07b-2d72-4902-899f-2f9fb165b8fd)  
  
## См. также  
 [Начало работы &#40;разработка решений Office в Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Доступность функций по типам приложений Office и проектов](../vsto/features-available-by-office-application-and-project-type.md)   
 [Образцы и пошаговые руководства разработки Office](../vsto/office-development-samples-and-walkthroughs.md)  
  
  
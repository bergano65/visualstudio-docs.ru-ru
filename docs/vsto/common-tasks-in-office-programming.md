---
title: "Общие задачи программирования Office | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, getting started
- FAQs (frequently asked questions) [Office development in Visual Studio]
- Office development in Visual Studio, frequently asked questions
ms.assetid: 7afc9bad-1d31-486e-beea-91e6d308cd67
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 9f3ed53011bca8d3ab7aa4f9d6be8e619ce1b8b5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="common-tasks-in-office-programming"></a>Общие задачи программирования Office
  Этот раздел призван помочь вам найти ответы на следующие категории часто задаваемых вопросов о программировании решений Office с помощью Visual Studio:  
  
-   [Установка и общие задачи](#projects)  
  
-   [Задачи по настройке пользовательского интерфейса](#ui)  
  
-   [Задачи автоматизации Excel](#excel)  
  
-   [Задачи автоматизации Word](#word)  
  
-   [Задачи работы с данными](#data)  
  
-   [Задачи управления документами на стороне сервера](#server)  
  
-   [Задачи по обеспечению безопасности](#security)  
  
-   [Задачи развертывания](#deployment)  
  
##  <a name="projects"></a> Setup and General Tasks  
  
-   [Как: Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
-   [Практическое руководство. Обновление решений Office](http://msdn.microsoft.com/en-us/a269e539-b717-4680-a568-2152b070347e)  
  
-   [How to: Install Office Primary Interop Assemblies](../vsto/how-to-install-office-primary-interop-assemblies.md).  
  
-   [How to: Target Office Applications Through Primary Interop Assemblies](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md).  
  
-   [Как: Создание обработчиков событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
-   [How to: Open Office Solutions without Running Code](../vsto/how-to-open-office-solutions-without-running-code.md).  
  
-   [How to: Set Up Configuration Information for an Office Solution](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md).  
  
-   [How to: Show the Developer Tab on the Ribbon](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
-   [How to: Show Add-in User Interface Errors](../vsto/how-to-show-add-in-user-interface-errors.md).  
  
##  <a name="ui"></a> User Interface Customization Tasks  
  
### <a name="controls-on-documents-and-worksheets"></a>Элементы управления в документах и на листах  
  
-   [How to: Add Windows Forms Controls to Office Documents](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).  
  
-   [How to: Add NamedRange Controls to Worksheets](../vsto/how-to-add-namedrange-controls-to-worksheets.md).  
  
-   [How to: Add ListObject Controls to Worksheets](../vsto/how-to-add-listobject-controls-to-worksheets.md).  
  
-   [How to: Add Windows Forms Controls to Office Documents](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).  
  
-   [How to: Add Content Controls to Word Documents](../vsto/how-to-add-content-controls-to-word-documents.md).  
  
-   [How to: Add Bookmark Controls to Word Documents](../vsto/how-to-add-bookmark-controls-to-word-documents.md).  
  
### <a name="task-panes-in-document-level-customizations"></a>Области задач в настройках уровня документа  
  
-   [Как: Добавление панели действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  
  
### <a name="task-panes-in-vsto-add-ins"></a>Области задач в надстройках VSTO  
  
-   [How to: Add a Custom Task Pane to an Application](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).  
  
### <a name="ribbon-customizations"></a>Настройки ленты  
  
-   [How to: Get Started Customizing the Ribbon](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
-   [Как: изменение положения вкладки на ленте](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md).  
  
-   [How to: Customize a Built-in Tab](../vsto/how-to-customize-a-built-in-tab.md).  
  
-   [Как: Добавление элементов управления в представление Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md).  
  
-   [How to: Export a Ribbon from the Ribbon Designer to Ribbon XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).  
  
### <a name="outlook-form-regions"></a>Области формы Outlook  
  
-   [How to: Add a Form Region to an Outlook Add-in Project](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
-   [How to: Prevent Outlook from Displaying a Form Region](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md).  
  
### <a name="custom-menus"></a>Настраиваемые меню  
  
-   [Как: Добавление команды в контекстное меню](../vsto/how-to-add-commands-to-shortcut-menus.md).  
  
##  <a name="excel"></a> Excel Automation Tasks  
  
-   [Как: программное отображение строки в ячейке листа](../vsto/how-to-programmatically-display-a-string-in-a-worksheet-cell.md).  
  
-   [Как: программным путем создания новых книг](../vsto/how-to-programmatically-create-new-workbooks.md).  
  
-   [Как: открытие книг](../vsto/how-to-programmatically-open-workbooks.md).  
  
-   [Как: программное Сохранение книг](../vsto/how-to-programmatically-save-workbooks.md).  
  
-   [Как: программное закрытие книг Excel](../vsto/how-to-programmatically-close-workbooks.md).  
  
-   [Как: программное добавление новых листов в книги Excel](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md).  
  
-   [Как: программное скрытие листов Excel](../vsto/how-to-programmatically-hide-worksheets.md).  
  
-   [Как: программное перемещение листов в книгах](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md).  
  
-   [Как: программная Защита книг](../vsto/how-to-programmatically-protect-workbooks.md).  
  
-   [Как: ссылки на диапазоны листов в коде программными средствами](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md).  
  
-   [Как: программное применение стилей к диапазонам в книгах](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md).  
  
-   [Как: программное изменение форматирования в строках листа, содержащих выбранные ячейки](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md).  
  
-   [Как: программный поиск текста в диапазонах листа](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md).  
  
-   [Как: программная печать листов](../vsto/how-to-programmatically-print-worksheets.md).  
  
-   [Как: программное выполнение вычислений Excel](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md).  
  
-   [Как: программная сортировка данных на листах](../vsto/how-to-programmatically-sort-data-in-worksheets.md).  
  
##  <a name="word"></a> Word Automation Tasks  
  
-   [Как: программное создание документов](../vsto/how-to-programmatically-create-new-documents.md).  
  
-   [Как: Открытие существующих документов](../vsto/how-to-programmatically-open-existing-documents.md).  
  
-   [Как: программное сохранение документов](../vsto/how-to-programmatically-save-documents.md).  
  
-   [Как: программное закрытие документов](../vsto/how-to-programmatically-close-documents.md).  
  
-   [Как: программная Вставка текста в документы Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md).  
  
-   [Как: программное определение и выделение диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md).  
  
-   [Как: программным образом сброс диапазонов в документах Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md).  
  
-   [Как: программное форматирование текста в документах](../vsto/how-to-programmatically-format-text-in-documents.md).  
  
-   [How to: Add XMLNode Controls to Word Documents](../vsto/how-to-add-xmlnode-controls-to-word-documents.md).  
  
-   [Как: программное обновление текста закладки](../vsto/how-to-programmatically-update-bookmark-text.md).  
  
-   [Как: программный поиск и замена текста в документах](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md).  
  
-   [Как: программная печать документов](../vsto/how-to-programmatically-print-documents.md).  
  
-   [Как: программное создание таблиц Word](../vsto/how-to-programmatically-create-word-tables.md).  
  
-   [Как: программным образом добавить строки и столбцы в таблицы Word](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md).  
  
-   [Как: программный подсчет символов в документах](../vsto/how-to-programmatically-count-characters-in-documents.md).  
  
##  <a name="data"></a> Data Tasks  
  
### <a name="data-bound-controls"></a>Элементы управления с привязкой к данным  
  
-   [How to: Populate Worksheets with Data from a Database](../vsto/how-to-populate-worksheets-with-data-from-a-database.md).  
  
-   [How to: Populate Documents with Data from a Database](../vsto/how-to-populate-documents-with-data-from-a-database.md).  
  
-   [How to: Populate Documents with Data from Services](../vsto/how-to-populate-documents-with-data-from-services.md).  
  
-   [How to: Populate Documents with Data from Objects](../vsto/how-to-populate-documents-with-data-from-objects.md).  
  
-   [How to: Populate Documents with Data from a Database](../vsto/how-to-populate-documents-with-data-from-a-database.md).  
  
-   [How to: Populate Documents with Data from Services](../vsto/how-to-populate-documents-with-data-from-services.md).  
  
-   [How to: Update a Data Source with Data from a Host Control](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).  
  
### <a name="cached-data-in-document-level-solutions"></a>Кэшированные данные в решениях на уровне документа  
  
-   [How to: Cache Data for Use Offline or on a Server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   [How to: Programmatically Cache a Data Source in an Office Document](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).  
  
-   [How to: Cache Data in a Password-Protected Document](../vsto/how-to-cache-data-in-a-password-protected-document.md).  
  
### <a name="custom-xml-data"></a>Пользовательские данные XML  
  
-   [How to: Add Custom XML Parts to Document-Level Customizations](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md).  
  
-   [How to: Add Custom XML Parts to Documents by Using VSTO Add-Ins](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md).  
  
##  <a name="server"></a> Server-side Document Management Tasks  
  
-   [Как: удаление расширений управляемого кода из документов](../vsto/how-to-remove-managed-code-extensions-from-documents.md).  
  
-   [Как: вложение расширений управляемого кода в документы](../vsto/how-to-attach-managed-code-extensions-to-documents.md).  
  
##  <a name="security"></a> Security Tasks  
  
-   [Как: подписывание решений Office](../vsto/how-to-sign-office-solutions.md).  
  
##  <a name="deployment"></a> Deployment Tasks  
  
-   [Практическое руководство. Публикация решения Office с помощью ClickOnce](http://msdn.microsoft.com/en-us/2b6c247e-bc04-4ce4-bb64-c4e79bb3d5b8)  
  
-   [Практическое руководство. Публикация решения Office уровня документа на сервере SharePoint с помощью ClickOnce](http://msdn.microsoft.com/en-us/2408e809-fb78-42a1-9152-00afa1522e58)  
  
-   [Практическое руководство. Установка решения Office ClickOnce](http://msdn.microsoft.com/en-us/14702f48-9161-4190-994c-78211fe18065)  
  
-   [Практическое руководство. Установка необходимых компонентов на компьютерах конечных пользователей для запуска решений Office](http://msdn.microsoft.com/en-us/74dd2c52-838f-4abf-b2b4-4d7b0c2a0a98)  
  
-   [Практическое руководство. Подготовка служб IIS для развертывания решений Office](http://msdn.microsoft.com/en-us/f62bce70-81d4-4f8b-86e6-2f2afec5d9b4)  
  
-   [Практическое руководство. Обновление развернутых решений Office](http://msdn.microsoft.com/en-us/be96db53-b6ea-46ab-b8d9-b76b098b3b13)  
  
-   [Практическое руководство. Изменение пути установки решения Office](http://msdn.microsoft.com/en-us/d0eaa07b-2d72-4902-899f-2f9fb165b8fd)  
  
## <a name="see-also"></a>См. также  
 [Приступая к работе &#40; разработка решений Office в Visual Studio &#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Доступность функций по типам приложений Office и проектов](../vsto/features-available-by-office-application-and-project-type.md)   
 [Примеры разработки решений Office и пошаговые руководства](../vsto/office-development-samples-and-walkthroughs.md)  
  
  
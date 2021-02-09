---
title: Распространенные задачи в программировании Office
description: Узнайте, как программировать данные в настройке на уровне документа без использования объектной модели Microsoft Office Word или Office Excel.
ms.custom: SEO-VS-2020SS
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, getting started
- FAQs (frequently asked questions) [Office development in Visual Studio]
- Office development in Visual Studio, frequently asked questions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 67b09d3881dcde1d404b7ff0c1096ced1ecb50ea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910604"
---
# <a name="common-tasks-in-office-programming"></a>Распространенные задачи в программировании Office
  Этот раздел призван помочь вам найти ответы на следующие категории часто задаваемых вопросов о программировании решений Office с помощью Visual Studio:

- [Настройка и общие задачи](#projects).

- [Задачи по настройке пользовательского интерфейса](#ui).

- [Задачи автоматизации Excel](#excel).

- [Задачи автоматизации Word](#word).

- [Задачи работы с данными](#data)

- [Задачи управления документами на стороне сервера](#server)

- [Задачи безопасности](#security).

- [Задачи развертывания](#deployment).

## <a name="setup-and-general-tasks"></a><a name="projects"></a> Настройка и общие задачи

- [Руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

- [Руководство. Обновление решений Office](/previous-versions/4bez6837(v=vs.140)).

- [Руководство. Установка основных сборок взаимодействия Office](../vsto/how-to-install-office-primary-interop-assemblies.md).

- Пошаговое [руководство. Назначение приложений Office через основные сборки взаимодействия](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md).

- [Как создавать обработчики событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

- [Руководство. Открытие решений Office без выполнения кода](../vsto/how-to-open-office-solutions-without-running-code.md).

- [Инструкции. Настройка сведений о конфигурации для решения Office](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md).

- [Как отобразить вкладку "Разработчик" на ленте](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

- [Пошаговое руководство. Отображение ошибок пользовательского интерфейса надстройки](../vsto/how-to-show-add-in-user-interface-errors.md).

## <a name="user-interface-customization-tasks"></a><a name="ui"></a> Задачи настройки пользовательского интерфейса

### <a name="controls-on-documents-and-worksheets"></a>Элементы управления в документах и листах

- [Добавление Windows Forms элементов управления в документы Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).

- [Как добавить элементы управления NamedRange в листы](../vsto/how-to-add-namedrange-controls-to-worksheets.md).

- [Как добавить элементы управления ListObject на листы](../vsto/how-to-add-listobject-controls-to-worksheets.md).

- [Добавление Windows Forms элементов управления в документы Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).

- [Как добавить элементы управления содержимым в документы Word](../vsto/how-to-add-content-controls-to-word-documents.md).

- [Руководство. Добавление элементов управления Bookmark в документы Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md).

### <a name="task-panes-in-document-level-customizations"></a>Области задач в настройках уровня документа

- [Руководство. Добавление панели действий в документы Word или книги Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).

### <a name="task-panes-in-vsto-add-ins"></a>Области задач в надстройках VSTO

- [Как добавить настраиваемую область задач в приложение](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).

### <a name="ribbon-customizations"></a>Настройки ленты

- [Как приступить к настройке ленты](../vsto/how-to-get-started-customizing-the-ribbon.md).

- [Как изменить позицию вкладки на ленте](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md).

- [Пошаговое руководство. Настройка встроенной вкладки](../vsto/how-to-customize-a-built-in-tab.md).

- [Поэтапное руководство. Добавление элементов управления в представление Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md).

- [Как экспортировать ленту из конструктора лент в XML-ленту](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).

### <a name="outlook-form-regions"></a>Области формы Outlook

- [Как добавить область формы в проект надстройки Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

- [Как запретить приложению Outlook отображать область формы](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md).

### <a name="custom-menus"></a>Настраиваемые меню

- [Как добавлять команды в контекстные меню](../vsto/how-to-add-commands-to-shortcut-menus.md).

## <a name="excel-automation-tasks"></a><a name="excel"></a> Задачи автоматизации Excel

- [Руководство. программное отображение строки в ячейке листа](../vsto/how-to-programmatically-display-a-string-in-a-worksheet-cell.md).

- [Руководство. Программное создание новых книг](../vsto/how-to-programmatically-create-new-workbooks.md).

- [Как программно открывать книги](../vsto/how-to-programmatically-open-workbooks.md).

- [Как программно сохранять книги](../vsto/how-to-programmatically-save-workbooks.md).

- [Руководство. программное закрытие книг](../vsto/how-to-programmatically-close-workbooks.md).

- [Как программно добавлять новые листы в книги](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md).

- [Как программно скрыть листы](../vsto/how-to-programmatically-hide-worksheets.md).

- [Руководство. Программное перемещение листов в книгах](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md).

- [Как программно защитить книги](../vsto/how-to-programmatically-protect-workbooks.md).

- [Как программно ссылаться на диапазоны листов в коде](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md).

- [Руководство. Программное применение стилей к диапазонам в книгах](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md).

- [Руководство. Программное изменение форматирования в строках листа, содержащих выбранные ячейки](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md).

- [Руководство. Программный поиск текста в диапазонах листа](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md).

- [Как печатать листы программным способом](../vsto/how-to-programmatically-print-worksheets.md).

- [Руководство. программное выполнение вычислений Excel](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md).

- [Руководство. Программная сортировка данных на листах](../vsto/how-to-programmatically-sort-data-in-worksheets.md).

## <a name="word-automation-tasks"></a><a name="word"></a> Задачи автоматизации Word

- [Руководство. Программное создание новых документов](../vsto/how-to-programmatically-create-new-documents.md).

- [Руководство. Программное открытие существующих документов](../vsto/how-to-programmatically-open-existing-documents.md).

- [Практические руководства. Программное сохранение документов](../vsto/how-to-programmatically-save-documents.md).

- [Руководство. программное закрытие документов](../vsto/how-to-programmatically-close-documents.md).

- [Инструкции. Программная вставка текста в документы Word](../vsto/how-to-programmatically-insert-text-into-word-documents.md).

- [Руководство. Программное определение и выбор диапазонов в документах](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md).

- [Руководство. Программный сброс диапазонов в документах Word](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md).

- [Руководство. Программное форматирование текста в документах](../vsto/how-to-programmatically-format-text-in-documents.md).

- [Руководство. Добавление элементов управления XMLNode в документы Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md).

- [Руководство. Программное обновление текста закладок](../vsto/how-to-programmatically-update-bookmark-text.md).

- [Руководство. Программный поиск и замена текста в документах](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md).

- [Практические руководства. Программная печать документов](../vsto/how-to-programmatically-print-documents.md).

- [Руководство. Программное создание таблиц Word](../vsto/how-to-programmatically-create-word-tables.md).

- [Руководство. Программное добавление строк и столбцов в таблицы Word](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md).

- [Как программно считать символы в документах](../vsto/how-to-programmatically-count-characters-in-documents.md).

## <a name="data-tasks"></a><a name="data"></a> Задачи с данными

### <a name="data-bound-controls"></a>Элементы управления с привязкой к данным

- [Как заполнять листы данными из базы данных](../vsto/how-to-populate-worksheets-with-data-from-a-database.md).

- [Руководство. Заполнение документов данными из базы данных](../vsto/how-to-populate-documents-with-data-from-a-database.md).

- [Руководство. Заполнение документов данными из служб](../vsto/how-to-populate-documents-with-data-from-services.md).

- [Руководство. Заполнение документов данными из объектов](../vsto/how-to-populate-documents-with-data-from-objects.md).

- [Руководство. Заполнение документов данными из базы данных](../vsto/how-to-populate-documents-with-data-from-a-database.md).

- [Руководство. Заполнение документов данными из служб](../vsto/how-to-populate-documents-with-data-from-services.md).

- [Руководство. Обновление источника данных с помощью данных из элемента управления ведущего приложения](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

### <a name="cached-data-in-document-level-solutions"></a>Кэшированные данные в решениях уровня документа

- [Как кэшировать данные для использования в автономном режиме или на сервере](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- [Руководство. программный кэш источника данных в документе Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).

- [Пошаговое руководство. кэширование данных в документе, защищенном паролем](../vsto/how-to-cache-data-in-a-password-protected-document.md).

### <a name="custom-xml-data"></a>Пользовательские данные XML

- [Как добавлять пользовательские XML-части в настройки уровня документа](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md).

- [Инструкции. Добавление пользовательских XML-частей в документы с помощью надстроек VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md).

## <a name="server-side-document-management-tasks"></a><a name="server"></a> Задачи управления документами на стороне сервера

- [Руководство. Удаление расширений управляемого кода из документов](../vsto/how-to-remove-managed-code-extensions-from-documents.md).

- [Как присоединить расширения управляемого кода к документам](../vsto/how-to-attach-managed-code-extensions-to-documents.md).

## <a name="security-tasks"></a><a name="security"></a> Задачи безопасности

- [Практические руководства. Подписывание решений Office](../vsto/how-to-sign-office-solutions.md).

## <a name="deployment-tasks"></a><a name="deployment"></a> Задачи развертывания

- [Инструкции. Публикация решения Office с помощью ClickOnce](/previous-versions/bb386095(v=vs.110)).

- [Инструкции. Публикация решения Office на уровне документа на сервере SharePoint с помощью ClickOnce](/previous-versions/bb608595(v=vs.110)).

- [Руководство. Установка решения ClickOnce для Office](/previous-versions/bb608592(v=vs.110)).

- [Руководство. Установка необходимых компонентов на компьютерах конечных пользователей для запуска решений Office](/previous-versions/bb608608(v=vs.110)).

- [Руководство. Подготовка служб IIS к развертыванию решений Office](/previous-versions/bb608629(v=vs.110)).

- [Руководство. Обновление развернутых решений Office](/previous-versions/bb157871(v=vs.110)).

- [Как изменить путь установки решения Office](/previous-versions/bb608626(v=vs.110)).

## <a name="see-also"></a>См. также раздел
- [Приступая к работе &#40;разработке решений Office в Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Возможности, доступные по типам приложений Office и проектов](../vsto/features-available-by-office-application-and-project-type.md)
- [Примеры и пошаговые руководства по разработке решений Office](../vsto/office-development-samples-and-walkthroughs.md)
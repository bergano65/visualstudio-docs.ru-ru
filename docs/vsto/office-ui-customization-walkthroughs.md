---
title: Пошаговые руководства по настройке пользовательского интерфейса Office
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- actions panes, walkthroughs
- smart documents, walkthroughs
- walkthroughs [Office development in Visual Studio], smart tags
- walkthroughs [Office development in Visual Studio], action panes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 95561f1404da1efd71ff3418f9154392f393795c
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56596598"
---
# <a name="office-ui-customization-walkthroughs"></a>Пошаговые руководства по настройке пользовательского интерфейса Office
  В приведенных ниже пошаговых руководствах описываются способы настройки пользовательского интерфейса приложений Microsoft Office с помощью настроек на уровне документа и надстроек VSTO.

## <a name="actions-pane-walkthroughs"></a>Пошаговые руководства по панели действий
- [Пошаговое руководство: Вставка текста в документ из панели действий](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md) показано, как создать панель действий в документе Word. Область действий содержит два элемента управления, которые обеспечивают передачу вводимых пользователем данных в документ.

- [Пошаговое руководство: Привязка данных к элементам управления в панели действий Word](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md) демонстрируется способ привязки элементов управления в панели действий в Word к данным. Элементы управления показывают отношение «Основной/подробности» между таблицами в базе данных SQL Server.

- [Пошаговое руководство: Привязка данных к элементам управления в панели действий Excel](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md) описывается добавление элементов управления, привязанных к источнику данных в панель действий в Excel.

## <a name="custom-task-pane-walkthroughs"></a>Пошаговые руководства по панели задач
- [Пошаговое руководство: Автоматизация приложения с настраиваемой области задач](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md) демонстрируется создание настраиваемой области задач, содержащей элемент управления, который автоматизирует ведущего приложения, когда пользователь щелкает элемент управления.

- [Пошаговое руководство: Синхронизация настраиваемой области задач с кнопкой на ленте](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md) демонстрируется создание настраиваемой области задач, пользователи могут скрывать и отображать, щелкая выключатель на ленте.

- [Пошаговое руководство: Отображение настраиваемых областей задач с сообщениями электронной почты в Outlook](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md) показано, как отобразить уникальный экземпляр настраиваемой области задач для каждого сообщения электронной почты, созданного или открытого в Outlook.

## <a name="ribbon-walkthroughs"></a>Пошаговые руководства по ленте
- [Пошаговое руководство: Создание настраиваемой вкладки с помощью конструктора лент](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md) демонстрируется создание настраиваемой вкладки на ленте с помощью конструктора лент. Вкладка содержит кнопку, которую можно использовать для скрытия или отображения области действий.

- [Пошаговое руководство: Обновления элементов управления на ленте во время выполнения](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md) показано, как использовать объектную модель ленты для обновления элементов управления на ленте после загрузки ленты в приложение Office.

- [Пошаговое руководство: Создание настраиваемой вкладки с помощью XML-код ленты](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md) демонстрируется создание настраиваемой вкладки на ленте с помощью XML-ленты вместо использования конструктора лент.

## <a name="controls-on-word-documents"></a>Элементы управления в документах Word
- [Пошаговое руководство: Добавление элементов управления в документ во время выполнения в надстройке VSTO](../vsto/walkthrough-adding-controls-to-a-document-at-run-time-in-a-vsto-add-in.md) демонстрируется добавление элементов управления в документ с помощью надстройки VSTO.

- [Пошаговое руководство: Изменение форматирования документа с использованием элементов управления CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md) демонстрируется изменение форматирования в документ Word с помощью флажков в настройке уровня документа.

- [Пошаговое руководство: Отображать текст в текстовом поле документа с помощью кнопки](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md) демонстрируется использование кнопок и текстовых полей в документах Word.

- [Пошаговое руководство: Обновление диаграммы в документе, с помощью переключателей](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md) показано, как изменить стили диаграммы в документ Word с помощью переключателей в настройке уровня документа.

## <a name="controls-on-excel-worksheets"></a>Элементы управления на листах Excel
- [Пошаговое руководство: Добавление элементов управления на лист во время выполнения в проекте надстройки VSTO](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md) показано, как добавлять элементы управления на лист с помощью надстройки VSTO.

- [Пошаговое руководство: Изменение форматирования листа с использованием элементов управления CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md) демонстрируются основные принципы использования флажков на листе Excel для изменения форматирования.

- [Пошаговое руководство: Отображать текст в текстовом поле на листе с помощью кнопки](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md) демонстрируются основные принципы использования кнопок и текстовых полей на листах Excel.

- [Пошаговое руководство: Обновление диаграммы на листе с помощью переключателей](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md) описываются основные принципы изменения стилей диаграмм с помощью переключателей на листе Excel.

## <a name="see-also"></a>См. также
- [Пошаговое руководство с использованием Word](../vsto/walkthroughs-using-word.md)
- [Пошаговые руководства с помощью Excel](../vsto/walkthroughs-using-excel.md)
- [Данные в пошаговых руководствах для решений Office](../vsto/data-in-office-solutions-walkthroughs.md)
- [Пошаговые руководства по безопасности и развертывания](../vsto/security-and-deployment-walkthroughs.md)
- [Начало работы &#40;разработка решений Office в Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Общие задачи программирования Office](../vsto/common-tasks-in-office-programming.md)
- [Разработка и создание решений Office](../vsto/designing-and-creating-office-solutions.md)

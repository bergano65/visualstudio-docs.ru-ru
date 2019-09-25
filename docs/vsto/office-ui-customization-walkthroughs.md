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
ms.openlocfilehash: e961479fc500e53133c62337478368878bf26893
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/25/2019
ms.locfileid: "71254131"
---
# <a name="office-ui-customization-walkthroughs"></a>Пошаговые руководства по настройке пользовательского интерфейса Office
  В приведенных ниже пошаговых руководствах описываются способы настройки пользовательского интерфейса приложений Microsoft Office с помощью настроек на уровне документа и надстроек VSTO.

## <a name="actions-pane-walkthroughs"></a>Пошаговые руководства по панели действий
- [Пошаговое руководство: Вставка текста в документ из панели](../vsto/walkthrough-inserting-text-into-a-document-from-an-actions-pane.md) действий демонстрирует создание панели действий в документе Word. Область действий содержит два элемента управления, которые обеспечивают передачу вводимых пользователем данных в документ.

- [Пошаговое руководство: Привязка данных к элементам управления на панели](../vsto/walkthrough-binding-data-to-controls-on-a-word-actions-pane.md) действий Word демонстрирует, как привязывать элементы управления на панели действий в Word к данным. Элементы управления показывают отношение «Основной/подробности» между таблицами в базе данных SQL Server.

- [Пошаговое руководство: Привязка данных к элементам управления на панели](../vsto/walkthrough-binding-data-to-controls-on-an-excel-actions-pane.md) действий Excel описывает добавление элементов управления, привязанных к источнику данных, к панели действий в Excel.

## <a name="custom-task-pane-walkthroughs"></a>Пошаговые руководства по настраиваемой области задач
- [Пошаговое руководство: Автоматизация приложения из настраиваемой области](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md) задач демонстрирует создание настраиваемой области задач, содержащей элемент управления, который автоматизирует ведущее приложение, когда пользователь щелкает элемент управления.

- [Пошаговое руководство: Синхронизация настраиваемой области задач с кнопкой](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md) на ленте демонстрирует создание настраиваемой области задач, которую пользователи могут скрывать или отображать, щелкая выключатель на ленте.

- [Пошаговое руководство: Отображение настраиваемых областей задач с сообщениями электронной почты](../vsto/walkthrough-displaying-custom-task-panes-with-e-mail-messages-in-outlook.md) в Outlook показывает, как отобразить уникальный экземпляр настраиваемой области задач для каждого сообщения электронной почты, созданного или открытого в Outlook.

## <a name="ribbon-walkthroughs"></a>Пошаговые руководства по лентам
- [Пошаговое руководство: Создание настраиваемой вкладки с помощью конструктора](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md) ленты демонстрирует создание настраиваемой вкладки ленты с помощью конструктора лент. Вкладка содержит кнопку, которую можно использовать для скрытия или отображения области действий.

- [Пошаговое руководство: Обновление элементов управления на ленте во время](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md) выполнения демонстрирует использование объектной модели Ribbon для обновления элементов управления на ленте после загрузки ленты в приложение Office.

- [Пошаговое руководство: Создание настраиваемой вкладки с помощью Ribbon XML](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md) демонстрирует создание настраиваемой вкладки ленты с помощью Ribbon XML вместо конструктора ленты.

## <a name="controls-on-word-documents"></a>Элементы управления в документах Word
- [Пошаговое руководство: Добавление элементов управления в документ во время выполнения в надстройке](../vsto/walkthrough-adding-controls-to-a-document-at-run-time-in-a-vsto-add-in.md) VSTO демонстрирует добавление элементов управления в документ с помощью надстройки VSTO.

- [Пошаговое руководство: Изменение форматирования документа с помощью элементов](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md) управления CheckBox демонстрируется изменение форматирования в документе Word с помощью флажков в настройке уровня документа.

- [Пошаговое руководство: Отображение текста в текстовом поле документа с помощью кнопки](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md) демонстрируется использование кнопок и текстовых полей в документах Word.

- [Пошаговое руководство: Обновление диаграммы в документе с помощью](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md) переключателей демонстрируется изменение стилей диаграммы в документе Word с помощью переключателей в настройке уровня документа.

## <a name="controls-on-excel-worksheets"></a>Элементы управления на листах Excel
- [Пошаговое руководство: Добавление элементов управления на лист во время выполнения в проекте](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md) надстройки VSTO демонстрирует добавление элементов управления на лист с помощью надстройки VSTO.

- [Пошаговое руководство: Изменение форматирования листа с помощью элементов](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md) управления CheckBox демонстрирует основные принципы использования флажков на листе Excel для изменения форматирования.

- [Пошаговое руководство: Отображение текста в текстовом поле листа с помощью кнопки](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md) демонстрирует основы использования кнопок и текстовых полей на листах Excel.

- [Пошаговое руководство: Обновление диаграммы на листе с помощью](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md) переключателей показывает основы изменения стилей диаграмм с помощью переключателей на листе Excel.

## <a name="see-also"></a>См. также
- [Пошаговые руководства с использованием Word](../vsto/walkthroughs-using-word.md)
- [Пошаговые руководства с использованием Excel](../vsto/walkthroughs-using-excel.md)
- [Пошаговые руководства по данным в решениях Office](../vsto/data-in-office-solutions-walkthroughs.md)
- [Пошаговые руководства по безопасности и развертыванию](../vsto/security-and-deployment-walkthroughs.md)
- [Начало работы &#40;с разработкой Office в Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Распространенные задачи в программировании Office](../vsto/common-tasks-in-office-programming.md)
- [Разработка и создание решений Office](../vsto/designing-and-creating-office-solutions.md)

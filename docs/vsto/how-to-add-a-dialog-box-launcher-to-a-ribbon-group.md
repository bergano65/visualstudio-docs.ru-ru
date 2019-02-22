---
title: Практическое руководство. Добавление кнопки запуска диалогового окна в группу ленты
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- dialog box launcher [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], dialog box launcher
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: aa12fdc3eea5c353071fb4a80e2c99f2f9e060c2
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56629954"
---
# <a name="how-to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Практическое руководство. Добавление кнопки запуска диалогового окна в группу ленты
  Кнопка вызова диалогового окна можно добавить в любую группу на ленте. Диалогового представляет собой небольшой значок, который отображается в группе. Пользователь нажимает эту кнопку, чтобы открыть диалоговых или области задач, которые предоставляют дополнительные возможности, относящиеся к группе.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Добавление кнопки запуска диалогового окна в группу ленты

1.  Выберите файл кода ленты (*.vb* или *.cs* файл) в **обозревателе решений**.

2.  На **представление** меню, щелкните **конструктор**.

3.  В конструкторе лент щелкните правой кнопкой мыши любую группу и нажмите кнопку **добавить средство запуска диалогового окна**.

     Добавьте код для <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick> событий группы, чтобы открыть диалоговое окно пользовательских или встроенных.

## <a name="see-also"></a>См. также
- [Обзор ленты](../vsto/ribbon-overview.md)
- [Доступ к ленте во время выполнения](../vsto/accessing-the-ribbon-at-run-time.md)
- [Примеры разработки решений Office и пошаговые руководства](../vsto/office-development-samples-and-walkthroughs.md)
- [Конструктор лент](../vsto/ribbon-designer.md)
- [Обзор объектной модели ленты](../vsto/ribbon-object-model-overview.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Практическое руководство. Экспорт лент из конструктора лент в XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Практическое руководство. Изменение положения вкладки на ленте](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Практическое руководство. Настройка встроенной вкладки](../vsto/how-to-customize-a-built-in-tab.md)
- [Практическое руководство. Добавление элементов управления в представление backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Настройка ленты для Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Практическое руководство. Приступая к настройке ленты](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Практическое руководство. Показывать ошибки надстройки пользовательского интерфейса](../vsto/how-to-show-add-in-user-interface-errors.md)
- [Пошаговое руководство: Создание настраиваемой вкладки с помощью конструктора лент](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Пошаговое руководство: Обновления элементов управления на ленте во время выполнения](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Пошаговое руководство: Создание настраиваемой вкладки с помощью XML-ленты](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)

---
title: Как добавить средство запуска диалогового окна в группу ленты
description: Можно добавить средство запуска диалогового окна в любую группу на ленте, которая может открывать связанные диалоговые окна или области задач, предоставляющие дополнительные параметры, связанные с группой.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- dialog box launcher [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], dialog box launcher
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d8e04b7549d1b6a458f0993804946502f55f0165
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99942286"
---
# <a name="how-to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Как добавить средство запуска диалогового окна в группу ленты
  Можно добавить средство запуска диалогового окна в любую группу на ленте. Средство запуска диалогового окна — это маленький значок, отображаемый в группе. Пользователи щелкают этот значок, чтобы открыть связанные диалоговые окна или области задач, предоставляющие дополнительные параметры, связанные с группой.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Добавление средства запуска диалогового окна в группу ленты

1. Выберите файл кода ленты (*VB* или *CS* -файл) в **Обозреватель решений**.

2. В меню **вид** выберите **конструктор**.

3. В конструкторе лент щелкните правой кнопкой мыши любую группу и выберите команду **Добавить диалогбокслаунчер**.

     Добавьте код в <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick> событие группы, чтобы открыть настраиваемое или встроенное диалоговое окно.

## <a name="see-also"></a>См. также раздел
- [Общие сведения о ленте](../vsto/ribbon-overview.md)
- [Доступ к ленте во время выполнения](../vsto/accessing-the-ribbon-at-run-time.md)
- [Примеры и пошаговые руководства по разработке решений Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Конструктор ленты](../vsto/ribbon-designer.md)
- [Общие сведения об объектной модели ленты](../vsto/ribbon-object-model-overview.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Практическое руководство. Экспорт лент из конструктора лент в XML-ленты](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Как изменить позицию вкладки на ленте](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Как настроить встроенную вкладку](../vsto/how-to-customize-a-built-in-tab.md)
- [Как добавить элементы управления в представление Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Настройка ленты для Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Как приступить к настройке ленты](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Пошаговое руководство. Отображение ошибок пользовательского интерфейса надстройки](../vsto/how-to-show-add-in-user-interface-errors.md)
- [Пошаговое руководство. Создание настраиваемой вкладки с помощью конструктора лент](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Пошаговое руководство. Обновление элементов управления на ленте во время выполнения](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Пошаговое руководство. Создание настраиваемой вкладки с помощью XML-ленты](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)

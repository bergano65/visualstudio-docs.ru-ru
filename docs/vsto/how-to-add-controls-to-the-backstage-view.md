---
title: 'Практическое руководство. Добавление элементов управления в представление Backstage '
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- customizing the Ribbon, menus
- controls, Ribbon
- menus, customizing
- Microsoft Office Button
- custom Ribbon, menus
- Ribbon, customizing
- Office button
- Ribbon, menus
- Microsoft Office Menu
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c4241464fe8a43af882fbdbad0f898838e8fd897
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62826786"
---
# <a name="how-to-add-controls-to-the-backstage-view"></a>Практическое руководство. Добавление элементов управления в представление Backstage
  Конструктор лент можно использовать для добавления элементов управления в меню, которое открывается при нажатии кнопки **файл** вкладки. При запуске приложения, элементы управления, добавляемые к **файл** вкладка отображается группа с именем **Add-ins**.

 Невозможно разместить элементы управления до или после встроенных элементов управления с помощью конструктора лент в Visual Studio. Встроенный элемент управления является элементом управления, который уже отображается в представлении Backstage. Если вы хотите разместить элементы управления до или после встроенных элементов управления, необходимо использовать XML ленты. Дополнительные сведения о **Лента (XML)**, см. в разделе [Ribbon XML](../vsto/ribbon-xml.md). Дополнительные сведения о настройке представления Backstage см. в разделе [введение в Office 2010 Backstage для разработчиков](http://go.microsoft.com/fwlink/?LinkId=182189) и [Настройка Office 2010 Backstage для разработчиков](http://go.microsoft.com/fwlink/?LinkId=182188).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-controls-to-backstage-view"></a>Добавление элементов управления в представление Backstage

1. Откройте элемент ленты в режиме конструктора.

     Сведения о добавлении **Лента (визуальный конструктор)** товара в проект, см. в разделе [как: Приступая к настройке ленты](../vsto/how-to-get-started-customizing-the-ribbon.md).

2. В конструкторе лент щелкните **файл** вкладки.

     Открывается конструктор меню. Эта поверхность не содержит все элементы управления.

3. Из **элементы управления ленты Office** вкладке **элементов**, перетащите один из следующих элементов управления в конструктор меню:

    - Кнопка

    - CheckBox

    - Коллекция

    - Меню

    - Separator

    - SplitButton

    - ToggleButton

4. Перетащите элементы управления для перемещения их новые положения в меню.

## <a name="see-also"></a>См. также
- [Обзор ленты](../vsto/ribbon-overview.md)
- [Конструктор лент](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Практическое руководство. Приступая к настройке ленты](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Пошаговое руководство: Создание настраиваемой вкладки с помощью конструктора лент](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)

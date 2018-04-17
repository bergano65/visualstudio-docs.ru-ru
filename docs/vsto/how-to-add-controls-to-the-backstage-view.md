---
title: 'Как: Добавление элементов управления в представление Backstage | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 1cdda3960363ba87e9434cd14077c7182a9f56c4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-add-controls-to-the-backstage-view"></a>Практическое руководство. Добавление элементов управления в представление Backstage
  Конструктор лент можно использовать для добавления элементов управления меню, которое открывается при нажатии кнопки **файл** вкладку при запуске приложения, элементы управления, добавляемые к **файл** вкладка отображается группа с именем  **Add-ins**.  
  
 Нельзя размещать элементы до или после встроенных элементов управления с помощью конструктора лент в Visual Studio. Встроенный элемент управления является элементом управления, который уже присутствует в представление Backstage. Если вы хотите разместить элементы управления до или после встроенных элементов управления, необходимо использовать XML-ленты. Дополнительные сведения о **Лента (XML)**, в разделе [XML-ленты](../vsto/ribbon-xml.md). Дополнительные сведения о настройке представления Backstage см. в разделе [введение в Office 2010 Backstage для разработчиков](http://go.microsoft.com/fwlink/?LinkId=182189) и [Настройка Office 2010 Backstage для разработчиков](http://go.microsoft.com/fwlink/?LinkId=182188).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-add-controls-to-backstage-view"></a>Добавление элементов управления в представление Backstage  
  
1.  Откройте элемент ленты в режиме конструктора.  
  
     Сведения о добавлении **Лента (визуальный конструктор)** в проект см. в разделе [как: работа с настройкой ленты](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
2.  В конструкторе лент щелкните **файл** вкладки.  
  
     Откроется конструктор меню. Поверхность проектирования не содержит все элементы управления.  
  
3.  Из **элементы управления ленты Office** вкладке **элементов**, перетащите любой из следующих элементов управления в конструктор меню:  
  
    -   Кнопка  
  
    -   CheckBox  
  
    -   Коллекции  
  
    -   Меню  
  
    -   Separator  
  
    -   SplitButton  
  
    -   ToggleButton  
  
4.  Перетащите элементы управления, чтобы переместить их в новые позиции в меню.  
  
## <a name="see-also"></a>См. также  
 [Обзор ленты](../vsto/ribbon-overview.md)   
 [Конструктор лент](../vsto/ribbon-designer.md)   
 [XML-ленты](../vsto/ribbon-xml.md)   
 [Как: работа с настройкой ленты](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Пошаговое руководство. Создание настраиваемой вкладки с помощью конструктора лент](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
  
  
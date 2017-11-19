---
title: "Как: изменение положения вкладки на ленте | Документы Microsoft"
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
helpviewer_keywords: Ribbon [Office development in Visual Studio], tabs
ms.assetid: 3f0906e3-9708-4136-ac49-986bc4c92ea4
caps.latest.revision: "26"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 40907d71bae8c8c25f06b3b1f3d4af8b9f79c385
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-change-the-position-of-a-tab-on-the-ribbon"></a>Практическое руководство. Изменение положения вкладки на ленте
  Можно изменить порядок пользовательских вкладок на ленту с помощью **редактор коллекции вкладок**. Пользовательские вкладки можно разместить до или после встроенной вкладки на ленте. Встроенная вкладка — это вкладка, которая уже находится на ленте приложения Microsoft Office. Например **данные** — Встроенная вкладка в Excel.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-change-the-order-of-tabs-on-the-ribbon"></a>Чтобы изменить порядок вкладок на ленте  
  
1.  Выберите файл кода ленты (VB или CS-файл) в **обозревателе решений**.  
  
2.  На **представление** меню, нажмите кнопку **конструктор**.  
  
3.  Щелкните правой кнопкой мыши в конструкторе лент и нажмите кнопку **свойства**.  
  
4.  В **свойства** выберите **вкладки** свойства, а затем нажмите кнопку с многоточием (![эллипс конструктора ASP.NET Mobile](../sharepoint/media/mwellipsis.gif "ASP.NET для мобильных устройств Эллипс конструктора")).  
  
     **Редактор коллекции вкладок** отображается.  
  
5.  В **редактор коллекции вкладок**в **члены** выберите вкладку, необходимо переместить и щелкните стрелку вверх или вниз для изменения порядка вкладок.  
  
### <a name="to-position-a-tab-before-or-after-a-built-in-tab-on-the-ribbon"></a>Размещение вкладки до или после встроенной вкладки на ленте  
  
1.  В конструкторе лент выберите настраиваемую вкладку.  
  
2.  В **свойства** окна, разверните **ControlId** свойство и затем убедитесь, что значение **ControlIdType** свойству **пользовательского**.  
  
3.  В **свойства** окна, разверните **позиции** свойство.  
  
4.  Задать **меню** соответствующее значение свойства:  
  
    -   **BeforeOfficeId** размещает группу перед указанной встроенной вкладки.  
  
    -   **AfterOfficeId** размещает группу после указанной встроенной вкладки.  
  
5.  Задать **OfficeId** свойство идентификатора встроенной вкладки.  
  
     Список идентификаторов элементов управления см. в разделе [файлы справки Office 2010: идентификаторы Office Fluent пользовательского интерфейса элемента управления](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
## <a name="see-also"></a>См. также  
 [Обзор ленты](../vsto/ribbon-overview.md)   
 [Конструктор лент](../vsto/ribbon-designer.md)   
 [XML-ленты](../vsto/ribbon-xml.md)   
 [Пошаговое руководство: Создание настраиваемой вкладки с помощью конструктора лент](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Пошаговое руководство. Создание настраиваемой вкладки с помощью XML-лент](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  
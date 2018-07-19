---
title: 'Практическое: изменение положения вкладки на ленте'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Ribbon [Office development in Visual Studio], tabs
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 08bbdf81023be466d30e49215fc0dbe1d3812f20
ms.sourcegitcommit: 34f7d23ce3bd140dcae875b602d5719bb4363ed1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/11/2018
ms.locfileid: "35255393"
---
# <a name="how-to-change-the-position-of-a-tab-on-the-ribbon"></a>Практическое: изменение положения вкладки на ленте
  Можно изменить порядок пользовательских вкладок на ленте с помощью **редактор коллекции вкладок**. Пользовательские вкладки можно разместить до или после встроенной вкладки на ленте. Встроенная вкладка — это вкладка, которая уже имеется на ленте приложения Microsoft Office. Например **данных** вкладка — это встроенная вкладка Excel.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-change-the-order-of-tabs-on-the-ribbon"></a>Чтобы изменить порядок вкладок на ленте  
  
1.  Выберите файл кода ленты (*.vb* или *.cs* файл) в **обозревателе решений**.  
  
2.  На **представление** меню, щелкните **конструктор**.  
  
3.  Щелкните конструктор лент правой кнопкой мыши, а затем нажмите кнопку **свойства**.  
  
4.  В **свойства** выберите **вкладки** свойство и затем нажмите кнопку с многоточием (![мобильных конструктора эллипс ASP.NET](../sharepoint/media/mwellipsis.gif "ASP.NET для мобильных устройств Эллипс конструктора")).  
  
     **Редактор коллекции вкладок** отображается.  
  
5.  В **редактор коллекции вкладок**в **члены** выберите вкладку, требуется переместить и щелкните стрелку вверх или вниз, чтобы изменить порядок вкладок.  
  
### <a name="to-position-a-tab-before-or-after-a-built-in-tab-on-the-ribbon"></a>Размещение вкладки до или после встроенной вкладки на ленте  
  
1.  В конструкторе лент выберите настраиваемую вкладку.  
  
2.  В **свойства** окне разверните **ControlId** свойство и затем убедитесь, что значение **ControlIdType** свойству **Custom**.  
  
3.  В **свойства** окне разверните **позиции** свойство.  
  
4.  Задайте **PositionType** свойство с соответствующим значением:  
  
    -   **BeforeOfficeId** размещает группу перед указанной встроенной вкладки.  
  
    -   **AfterOfficeId** размещает группу после указанной встроенной вкладки.  
  
5.  Задайте **OfficeId** свойства идентификатора из встроенной вкладки.  
  
     Список идентификаторов элементов управления, см. в разделе [файлы справки Office 2010: идентификаторы элементов управления интерфейса Office fluent пользователя](http://go.microsoft.com/fwlink/?LinkID=181052).  
  
## <a name="see-also"></a>См. также  
 [Обзор ленты](../vsto/ribbon-overview.md)   
 [Конструктор лент](../vsto/ribbon-designer.md)   
 [XML-ленты](../vsto/ribbon-xml.md)   
 [Пошаговое руководство: Создание настраиваемой вкладки с помощью конструктора лент](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Пошаговое руководство: Создание настраиваемой вкладки с помощью XML-ленты](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  
---
title: 'Как: экспорт ленты из конструктора лент в XML-ленты | Документы Microsoft'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, XML
- customizing the Ribbon, XML
- Ribbon [Office development in Visual Studio], XML
- Ribbon [Office development in Visual Studio], exporting
- XML [Office development in Visual Studio], Ribbon
- Ribbon Designer [Office development in Visual Studio]
- exporting Ribbon
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7aff56d1d7ee3533a83ef3edbdd8ba9271efd862
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Практическое руководство. Экспорт лент из конструктора лент в XML-ленты
  **Лента (визуальный конструктор)** элемент не поддерживает все типы настроек ленты. Для настройки ленты дополнительными способами, можно экспортировать ленту из конструктора XML-ленты и непосредственного редактирования XML.  
  
> [!NOTE]  
>  Не все свойства отображаются в XML-файле ленты. Дополнительные сведения см. в разделе [Обзор ленты](../vsto/ribbon-overview.md).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Для экспорта ленты из конструктора лент в XML-ленты  
  
1.  Щелкните правой кнопкой мыши файл кода ленты в **обозревателе решений**, а затем нажмите кнопку **конструктор представлений**.  
  
2.  Щелкните правой кнопкой мыши в конструкторе лент и нажмите кнопку **экспортировать ленту в XML**.  
  
     Visual Studio добавляет XML-файл ленты и файл кода XML ленты в проект.  
  
3.  В классе кода ленты разместите комментарии, начинающиеся с `TODO:`.  
  
4.  Скопируйте блок кода в этих комментариев к **ThisAddin**, **ThisWorkbook**, или **ThisDocument** класса, в зависимости от того, какой тип решения вы разрабатываете.  
  
     Этот код позволяет приложению Microsoft Office обнаружить и загрузить пользовательскую ленту. Дополнительные сведения см. в разделе [Ribbon XML](../vsto/ribbon-xml.md).  
  
5.  В **ThisAddin**, **ThisWorkbook**, или **ThisDocument** класса, раскомментируйте блок кода.  
  
     После отмены комментариев кода, он должен выглядеть примерно так. В этом примере класс ленты называется `MyRibbon`.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]  
  
6.  В файле кода ленты XML и найти `Ribbon Callbacks` области.  
  
     Это происходит, где вы записываете методы обратного вызова для обработки действий пользователя, например на нажатие кнопки.  
  
7.  Создайте метод обратного вызова для каждого обработчика события, записанного в коде конструктора лент.  
  
8.  Переместите весь свой код обработчика событий из обработчиков событий в методы обратного вызова и изменения кода для работы с моделью программирования расширения ленты (RibbonX).  
  
     Сведения о создании методов обратного вызова и использование модели программирования RibbonX см. в разделе [XML-ленты](../vsto/ribbon-xml.md).  
  
## <a name="see-also"></a>См. также  
 [Обзор ленты](../vsto/ribbon-overview.md)   
 [Конструктор лент](../vsto/ribbon-designer.md)   
 [XML-ленты](../vsto/ribbon-xml.md)   
 [Пошаговое руководство: Создание настраиваемой вкладки с помощью конструктора лент](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Пошаговое руководство. Создание настраиваемой вкладки с помощью XML-лент](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  
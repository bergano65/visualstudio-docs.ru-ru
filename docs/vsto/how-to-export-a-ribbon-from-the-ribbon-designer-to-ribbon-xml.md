---
title: Практическое руководство. Экспорт лент из конструктора лент в XML-ленты
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 17d6efe4aa18682c6777128113f6fa60347f8950
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63419497"
---
# <a name="how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Практическое руководство. Экспорт лент из конструктора лент в XML-ленты
  **Лента (визуальный конструктор)** элемент не поддерживает все типы настроек ленты. Чтобы расширенные способы настройки ленты можно экспорт ленты из конструктора XML-ленты и непосредственного редактирования XML.

> [!NOTE]
> Не все свойства отображаются в XML-файле ленты. Дополнительные сведения см. в разделе [Обзор ленты](../vsto/ribbon-overview.md).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml"></a>Чтобы Экспорт лент из конструктора лент в XML-ленты

1. Щелкните правой кнопкой мыши файл кода ленты в **обозревателе решений**, а затем нажмите кнопку **конструктор представлений**.

2. Щелкните конструктор лент правой кнопкой мыши, а затем нажмите кнопку **экспорт ленты в формат XML**.

     Visual Studio добавляет файл Ribbon XML и файл кода XML ленты в проект.

3. В классе кода ленты разместите комментарии, начинающиеся с `TODO:`.

4. Скопируйте блок кода в этих комментариях к **ThisAddin**, **ThisWorkbook**, или **ThisDocument** класса, в зависимости от того, какой тип решения при разработке.

     Этот код позволяет приложению Microsoft Office обнаружить и загрузить пользовательские ленты. Дополнительные сведения см. в разделе [Ribbon XML](../vsto/ribbon-xml.md).

5. В **ThisAddin**, **ThisWorkbook**, или **ThisDocument** класса, раскомментируйте блок кода.

     После вы раскомментируйте код, он должен выглядеть следующим образом. В этом примере класс ленты называется `MyRibbon`.

     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/CSharp/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../vsto/codesnippet/VisualBasic/Trin_Ribbon_Custom_Tab_XML_O12/ThisAddIn.vb#1)]

6. Переключитесь в файле кода XML-код ленты и найти `Ribbon Callbacks` регион.

     Это, где вы записываете методы обратного вызова для обработки действий пользователя, например на нажатие кнопки.

7. Создайте метод обратного вызова для каждого обработчика события, записанного в коде конструктора лент.

8. Переместите все код обработчика событий из обработчиков событий в методы обратного вызова и измените код для работы с моделью программирования расширения ленты (RibbonX).

     Сведения о создании методов обратного вызова и использование модели программирования RibbonX, см. в разделе [Ribbon XML](../vsto/ribbon-xml.md).

## <a name="see-also"></a>См. также
- [Обзор ленты](../vsto/ribbon-overview.md)
- [Конструктор лент](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Пошаговое руководство: Создание настраиваемой вкладки с помощью конструктора лент](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Пошаговое руководство: Создание настраиваемой вкладки с помощью XML-ленты](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)

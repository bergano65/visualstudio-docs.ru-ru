---
title: "Приступая к программированию настроек на уровне документа для Excel | Документы Microsoft"
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
helpviewer_keywords:
- Excel solutions in Visual Studio
- Excel projects [Office development in Visual Studio], getting started
ms.assetid: 8b73cf08-a173-4b49-b20f-2d2456dbe925
caps.latest.revision: "41"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1755aa5c8e54bd1b84e0f88ea70b4163f3a87af6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="getting-started-programming-document-level-customizations-for-excel"></a>Знакомство с программными настройками уровня документа для Excel
  Если вы только начинающие работу создания настроек на уровне документа для Microsoft Office Excel с помощью Visual Studio, вот что нужно знать.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
## <a name="understanding-how-document-level-customizations-for-excel-work"></a>Основные сведения о настройках уровня документа для Excel  
 Настройки уровня документа для Excel основана на отдельной книгой. Чтобы начать использовать настройки, конечный пользователь открывает книгу или создает ее из шаблона Excel. События в книге, например ввода в ячейках или нажатие кнопки и пункты меню можно вызывать методы обработки событий в сборке. При закрытии книги возможности, предоставленные в настройке больше недоступны в Excel только в документе, который содержит их.  
  
 Дополнительные сведения см. в разделе [архитектура настроек на уровне документа](../vsto/architecture-of-document-level-customizations.md).  
  
## <a name="creating-document-level-projects-for-excel"></a>Создание проектов уровня документа для Excel  
 Чтобы создать проект настройки уровня документа для Excel, используйте шаблон проекта книги Excel или шаблона Excel в **новый проект** диалоговое окно. Эти шаблоны включают в себя необходимые ссылки на сборки и файлы проекта.  
  
 Дополнительные сведения о создании проекта уровня документа для Excel см. в разделе [как: Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Дополнительные сведения о шаблонах проектов см. в разделе [Общие сведения о шаблонах проектов Office](../vsto/office-project-templates-overview.md).  
  
## <a name="programming-excel-workbooks-by-using-host-items-and-host-controls"></a>Программирование листов Excel с помощью ведущих элементов и элементов управления ведущего приложения  
 *Ведущие элементы* и *элементы управления ведущего приложения* являются классы, предоставляющие модель программирования для настроек уровня документа, созданных с помощью Visual Studio.  
  
 Ведущие элементы предоставляют точку входа для кода, а также могут выступать в качестве контейнеров для элементов управления ведущего приложения и элементы управления Windows Forms. В проектах уровня документа для Excel, эти ведущие элементы представлены в виде `ThisWorkbook`, `Sheet1`, `Sheet2`, и `Sheet3` классы.  
  
 Элементы управления ведущего приложения основаны на собственных объектов Excel, такие как список объектов и диапазоны. Элементы управления ведущего приложения предоставляют аналогичные функциональные возможности для собственных объектов Excel, но они также имеют новые события, поддержка конструктора и возможность привязки данных. Они отображаются как объекты первичного класса в коде проекта и IntelliSense, что упрощает ссылки на определенные объекты непосредственно в коде без необходимости перехода по объектной модели Excel.  
  
 Дополнительные сведения см. в следующих разделах:  
  
-   [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md)  
  
-   [Automating Excel by Using Extended Objects](../vsto/automating-excel-by-using-extended-objects.md)  
  
-   [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)  
  
## <a name="customizing-the-user-interface-of-excel"></a>Настройка пользовательского интерфейса Excel  
 Большинство решений Microsoft Office изменяют пользовательский интерфейс (UI) приложения Office, чтобы некоторые позволяют пользователям взаимодействовать с решением. Существует множество способов, в которых пользовательского интерфейса Excel можно изменить с помощью настройки уровня документа. Например можно добавить элементы управления на ленту, или можно отобразить панель действий. Дополнительные сведения см. в разделе [настройки пользовательского интерфейса Office](../vsto/office-ui-customization.md).  
  
 Можно также открыть книгу, связанные с проектом непосредственно в Visual Studio. Когда книга открыта в Visual Studio, можно изменить книгу с помощью пользовательского интерфейса Excel. Также можно использовать книгу как поверхность разработки, что дает возможность перетаскивать элементы управления на листах. Дополнительные сведения см. в разделе [проекты Office в среде Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="using-data-binding"></a>Использование привязки данных  
 Элементы управления ведущего приложения также присутствуют в списке элементов управления, которые можно перетаскивать из **источники данных** окна. Добавление элементов управления ведущего приложения в этом образом автоматически привязывает их к источнику данных, которая настраивается с помощью окна. Без написания кода, можно отобразить данные из базы данных, веб-служб и бизнес-объектов. Дополнительные сведения см. в разделе [привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
## <a name="next-steps"></a>Дальнейшие действия  
 Сведения о создании настроек уровня документа для Excel, в разделе [Пошаговое руководство: Создание вашей первой настройки уровня документа для Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md). В этом пошаговом руководстве представлены средства разработки Office в Visual Studio и модель программирования для настроек уровня документа для Excel.  
  
 Список разделов с пошаговыми руководствами для некоторых общих задач в проектах Excel см. в разделе [общие задачи программирования Office](../vsto/common-tasks-in-office-programming.md).  
  
## <a name="see-also"></a>См. также  
 [Как: Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Программирование настроек на уровне документа](../vsto/programming-document-level-customizations.md)   
 [Решения Excel](../vsto/excel-solutions.md)   
 [Пошаговое руководство: Создание первой настройки уровня документа для Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [Пошаговые руководства с использованием Excel](../vsto/walkthroughs-using-excel.md)   
 [Общие сведения о модели объектов Excel](../vsto/excel-object-model-overview.md)   
 [Написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md)  
  
  
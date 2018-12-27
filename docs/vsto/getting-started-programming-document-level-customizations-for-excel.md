---
title: Приступить к программированию настроек на уровне документа для Excel
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel solutions in Visual Studio
- Excel projects [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 808b463445934ecf5cc973b571b4b64d181eb692
ms.sourcegitcommit: a205ff1b389fba1803acd32c54df7feb0ef7a203
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/20/2018
ms.locfileid: "53646949"
---
# <a name="get-started-programming-document-level-customizations-for-excel"></a>Приступить к программированию настроек на уровне документа для Excel
  Если вы начальном этапе создания настроек уровня документа для Microsoft Office Excel с помощью Visual Studio, вот что вам необходимо знать.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
## <a name="understand-how-document-level-customizations-for-excel-work"></a>Понять настройках уровня документа для Excel  
 Настройки уровня документа для Excel основана на одну книгу. Чтобы начать настройку, конечный пользователь открывает книгу или создает ее из шаблона Excel. События в книге, например ввода в ячейках или нажатие кнопки и пункты меню, может вызывать методы обработки событий в сборке. При закрытии книги, функции, предоставленные в настройке больше не доступны в Excel только в документе, который содержит их.  
  
 Дополнительные сведения см. в разделе [архитектура настроек на уровне документа](../vsto/architecture-of-document-level-customizations.md).  
  
## <a name="create-document-level-projects-for-excel"></a>Создание проектов уровня документа для Excel  
 Чтобы создать настройку уровня документа для Excel, используйте шаблон проекта книги Excel или шаблон Excel в **новый проект** диалоговое окно. Эти шаблоны включают в себя необходимые ссылки на сборки и файлы проекта.  
  
 Дополнительные сведения о том, как создать проект уровня документа для Excel см. в разделе [как: Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Дополнительные сведения о шаблонах проектов см. в разделе [Общие сведения о шаблонах проектов Office](../vsto/office-project-templates-overview.md).  
  
## <a name="program-excel-workbooks-by-using-host-items-and-host-controls"></a>Программа книг Excel с помощью ведущих элементов и элементов управления ведущего приложения  
 *Ведущие элементы* и *элементы управления ведущего приложения* являются классами, предоставляющими модель программирования для настроек уровня документа, созданных с помощью Visual Studio.  
  
 Ведущие элементы предоставляют точку входа для кода, а также могут выступать в качестве контейнеров для элементов управления ведущего приложения и элементов управления Windows Forms. В проектах уровня документа для Excel, эти элементы узла представлены `ThisWorkbook`, `Sheet1`, `Sheet2`, и `Sheet3` классы.  
  
 Элементы управления ведущего приложения основаны на собственных объектов Excel, такие как список объектов и диапазоны. Элементы управления ведущего приложения предоставляют аналогичные функциональные возможности для собственных объектов Excel, но они также имеют новые события, поддержка конструктора и возможность привязки данных. Они отображаются как объекты первичного класса в коде проекта и IntelliSense, что позволяет проще ссылаться на определенные объекты непосредственно в коде без необходимости перехода по объектной модели Excel.  
  
 Дополнительные сведения см. в следующих разделах:  
  
-   [Программирование настроек уровня документа](../vsto/programming-document-level-customizations.md)  
  
-   [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)  
  
-   [Ведущие элементы и элементы управления](../vsto/host-items-and-host-controls-overview.md)  
  
## <a name="customize-the-user-interface-of-excel"></a>Настройка пользовательского интерфейса Excel  
 Большинство решений для Microsoft Office изменить пользовательский интерфейс (UI) приложения Office для какой-нибудь способ пользователям взаимодействовать с решением. Существует много способов, в которых пользовательского интерфейса Excel можно изменить с помощью настройки уровня документа. Например можно добавить элементы управления на ленту, или можно отобразить панель действий. Дополнительные сведения см. в разделе [настройки пользовательского интерфейса Office](../vsto/office-ui-customization.md).  
  
 Также можно открыть книгу, связанные с проектом непосредственно в Visual Studio. Если книга открыта в Visual Studio, можно изменить книгу с помощью пользовательского интерфейса Excel. Также можно использовать книгу как поверхность разработки, что дает возможность перетаскивать элементы управления на листах. Дополнительные сведения см. в разделе [проекты Office в среде Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="use-data-binding"></a>Использование привязки данных  
 Элементы управления ведущего приложения также находятся в списке элементов управления, которые можно перетаскивать из **источников данных** окна. Добавление элементов управления ведущего приложения в этом образом автоматически привязывает их к источнику данных, которая настраивается с помощью окна. Без написания кода, можно отобразить данные из базы данных, веб-служб и бизнес-объектов. Дополнительные сведения см. в разделе [привязки данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
## <a name="next-steps"></a>Следующие шаги  
 Узнайте, как создавать настройку на уровне документа для Excel, см. в разделе [Пошаговое руководство: Создание первой настройки уровня документа для Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md). В этом пошаговом руководстве представлены средства разработки Office в Visual Studio и модель программирования для настроек уровня документа для Excel.  
  
 Список разделов с пошаговыми руководствами некоторые распространенные задачи в проектах Excel, см. в разделе [общие задачи программирования Office](../vsto/common-tasks-in-office-programming.md).  
  
## <a name="see-also"></a>См. также  
 [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Программирование настроек уровня документа](../vsto/programming-document-level-customizations.md)   
 [Решения Excel](../vsto/excel-solutions.md)   
 [Пошаговое руководство: Создание первой настройки уровня документа для Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)   
 [Пошаговые руководства с помощью Excel](../vsto/walkthroughs-using-excel.md)   
 [Обзор объектной модели Excel](../vsto/excel-object-model-overview.md)   
 [Написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md)  
  
  
---
title: 'Excel: Приступая к программированию настроек уровня документа'
description: Узнайте, что нужно знать, чтобы приступить к созданию настроек уровня документа для Microsoft Office Excel с помощью Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel solutions in Visual Studio
- Excel projects [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1fb048fd015126e5438a007be1950cddffbac9e1
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846042"
---
# <a name="get-started-programming-document-level-customizations-for-excel"></a>Приступая к программированию настроек уровня документа для Excel
  Если вы только приступите к созданию настроек уровня документа для Microsoft Office Excel с помощью Visual Studio, вот что нужно знать.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="understand-how-document-level-customizations-for-excel-work"></a>Сведения о настройке уровня документа для работы с Excel
 Настройка уровня документа для Excel основана на одной книге. Чтобы начать работу с настройкой, конечный пользователь открывает книгу или создает книгу на основе шаблона Excel. События в книге, например ввод в ячейки или нажатие кнопок и пунктов меню, могут вызывать методы обработки событий в сборке. При закрытии книги функции, предоставляемые этой настройкой, больше не доступны в Excel, а только в документе, в котором они содержатся.

 Дополнительные сведения см. в разделе [Архитектура настроек на уровне документа](../vsto/architecture-of-document-level-customizations.md).

## <a name="create-document-level-projects-for-excel"></a>Создание проектов уровня документа для Excel
 Чтобы создать настройку на уровне документа для Excel, используйте шаблон "книга Excel" или "шаблон проекта Excel" в диалоговом окне " **Создание проекта** ". Эти шаблоны включают в себя необходимые ссылки на сборки и файлы проекта.

 Дополнительные сведения о создании проекта уровня документа для Excel см. в разделе [Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Дополнительные сведения о шаблонах проектов см. в разделе [Общие сведения о шаблонах проектов Office](../vsto/office-project-templates-overview.md).

## <a name="program-excel-workbooks-by-using-host-items-and-host-controls"></a>Программирование книг Excel с помощью ведущих элементов и элементов управления ведущего приложения
 *Ведущие элементы* и *элементы управления ведущего приложения* — это классы, предоставляющие модель программирования для настроек уровня документа, созданных с помощью Visual Studio.

 Ведущие элементы предоставляют точку входа для кода, а также могут действовать как контейнеры для элементов управления ведущего приложения и Windows Forms элементов управления. В проектах уровня документа для Excel эти ведущие элементы представлены `ThisWorkbook` `Sheet1` классами,, `Sheet2` и `Sheet3` .

 Элементы управления ведущего приложения основаны на собственных объектах Excel, таких как объекты списка и диапазоны. Элементы управления ведущего приложения предоставляют аналогичные функции для собственных объектов Excel, но они также имеют новые события, поддержку конструктора и возможность привязки данных. Они отображаются как объекты первого класса в коде проекта и IntelliSense, что упрощает обращение к конкретным объектам непосредственно в коде без необходимости перехода по объектной модели Excel.

 Дополнительные сведения см. в следующих разделах:

- [Программы настройки на уровне документа](../vsto/programming-document-level-customizations.md)

- [Автоматизация Excel с помощью расширенных объектов](../vsto/automating-excel-by-using-extended-objects.md)

- [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)

## <a name="customize-the-user-interface-of-excel"></a>Настройка пользовательского интерфейса Excel
 Большинство Microsoft Office решений изменяют пользовательский интерфейс приложения Office, чтобы предоставить пользователям возможность взаимодействовать с решением. Существует множество способов изменения пользовательского интерфейса Excel с помощью настройки уровня документа. Например, можно добавить элементы управления на ленту или отобразить панель действий. Дополнительные сведения см. в разделе [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md).

 Можно также открыть книгу, связанную с проектом, непосредственно в Visual Studio. Если книга открыта в Visual Studio, ее можно изменить с помощью пользовательского интерфейса Excel. Книгу также можно использовать в качестве области конструктора, что позволяет перетаскивать элементы управления на листы. Дополнительные сведения см. [в статье проекты Office в среде Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).

## <a name="use-data-binding"></a>Использовать привязку данных
 Элементы управления ведущего приложения также находятся в списке элементов управления, которые можно перетаскивать из окна **Источники данных** . Добавление элементов управления ведущего приложения таким образом автоматически привязывает их к источнику данных, настроенному с помощью окна. Без написания кода можно отображать данные из баз данных, веб-служб и бизнес-объектов. Дополнительные сведения см. [в разделе Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md).

## <a name="next-steps"></a>Дальнейшие действия
 Сведения о создании настройки уровня документа для Excel см. в разделе [Пошаговое руководство. Создание первой настройки уровня документа для Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md). В этом пошаговом руководстве рассматриваются средства разработки Office в Visual Studio и модель программирования для настроек на уровне документа Excel.

 Список разделов, в которых описаны некоторые распространенные задачи в проектах Excel, см. [в разделе Общие задачи в программировании Office](../vsto/common-tasks-in-office-programming.md).

## <a name="see-also"></a>См. также раздел
- [Как создавать проекты Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Программы настройки на уровне документа](../vsto/programming-document-level-customizations.md)
- [Решения Excel](../vsto/excel-solutions.md)
- [Пошаговое руководство. Создание первой настройки уровня документа для Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)
- [Пошаговые руководства с использованием Excel](../vsto/walkthroughs-using-excel.md)
- [Общие сведения об объектной модели Excel](../vsto/excel-object-model-overview.md)
- [Написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md)

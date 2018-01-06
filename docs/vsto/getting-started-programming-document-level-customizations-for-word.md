---
title: "Приступая к программированию настроек на уровне документа для Word | Документы Microsoft"
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
- Word solutions in Visual Studio
- Word projects [Office development in Visual Studio], getting started
ms.assetid: 30593c47-1658-4fca-b9a9-36fbdf73c901
caps.latest.revision: "44"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 12265c725480324c396d59d848e5269432bb5d6e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-programming-document-level-customizations-for-word"></a>Приступая к работе: программирование настроек уровня документа для Word
  Если вы только начинающие работу создания настроек на уровне документа для Microsoft Office Word с помощью Visual Studio, вот что нужно знать.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
## <a name="understanding-how-document-level-customizations-for-word-work"></a>Основные сведения о настройках уровня документа для Word  
 Каждая создаваемая настройка Word основана одного документа. Чтобы начать использовать настройки, конечный пользователь открывает документ или создает документ из шаблона Word. События в документе, например переместите курсор в конкретных областях или нажатие кнопки и пункты меню можно вызывать методы обработки событий в сборке. При закрытии документа возможности, предоставленные в настройке больше недоступны в Word.  
  
 Дополнительные сведения см. в разделе [архитектура настроек на уровне документа](../vsto/architecture-of-document-level-customizations.md).  
  
## <a name="creating-document-level-projects-for-word"></a>Создание проектов уровня документа для Word  
 Чтобы создать проект настройки уровня документа для Word, используйте шаблон проекта документа Word или шаблона Word в **новый проект** диалоговое окно. Эти шаблоны включают в себя необходимые ссылки на сборки и файлы проекта.  
  
 Дополнительные сведения о создании проекта уровня документа для Word см. в разделе [как: Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Дополнительные сведения о шаблонах проектов см. в разделе [Общие сведения о шаблонах проектов Office](../vsto/office-project-templates-overview.md).  
  
## <a name="programming-word-documents-by-using-host-items-host-controls"></a>Программирование документов Word с помощью элементов управления ведущего приложения узла элементов  
 *Ведущие элементы* и *элементы управления ведущего приложения* — это классы, которые предоставляют модель программирования для настроек на уровне документа.  
  
 Ведущие элементы предоставляют точку входа для кода, а также могут выступать в качестве контейнеров для элементов управления ведущего приложения и элементы управления Windows Forms. В проектах уровня документа для Word, ведущего элемента, представленного `ThisDocument` класса.  
  
 Элементы управления ведущего приложения основаны на собственных объектов Word, такие как элементы управления содержимым, закладки и XML-узлов. Элементы управления ведущего приложения предоставляют аналогичные функциональные возможности для собственных объектов Word, однако они обладают новые события, поддержка конструктора и возможность привязки данных. Они отображаются как объекты первичного класса в коде проекта и IntelliSense, что упрощает ссылки на определенные объекты непосредственно в коде без необходимости перехода по объектной модели Word.  
  
 Дополнительные сведения см. в следующих разделах:  
  
-   [Programming Document-Level Customizations](../vsto/programming-document-level-customizations.md)  
  
-   [Automating Word by Using Extended Objects](../vsto/automating-word-by-using-extended-objects.md)  
  
-   [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)  
  
## <a name="customizing-the-user-interface-of-word"></a>Настройка пользовательского интерфейса Word  
 Большинство решений Microsoft Office изменяют пользовательский интерфейс (UI) приложения Office, чтобы некоторые позволяют пользователям взаимодействовать с решением. Существует множество способов, в которых пользовательского интерфейса Word можно изменить с помощью настройки уровня документа. Например можно добавить элементы управления на ленту и может отображать панели действий. Дополнительные сведения см. в разделе [настройки пользовательского интерфейса Office](../vsto/office-ui-customization.md).  
  
 Можно также открыть документ, связанный с проектом непосредственно в Visual Studio. Если документ открыт в Visual Studio, можно изменить документ с помощью пользовательского интерфейса Word. Документ также можно использовать как рабочую область конструктора, который позволяет перетаскивать элементы управления. Дополнительные сведения см. в разделе [проекты Office в среде Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
## <a name="binding-controls-to-data"></a>Привязка элементов управления к данным  
 Элементы управления содержимым и <xref:Microsoft.Office.Tools.Word.Bookmark> управления находятся в списке элементов управления, которые можно перетаскивать из **источники данных** окна. Добавление элементов управления содержимым и закладок подобным образом автоматически привязывает их к источнику данных, которая настраивается с помощью окна. Без написания кода, можно отобразить данные из базы данных, служб и бизнес-объектов. Дополнительные сведения см. в разделе [привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md).  
  
## <a name="next-steps"></a>Следующие шаги  
 Дополнительные сведения о создании настройки на уровне документа для Word, см [Пошаговое руководство: создание вашего первого уровня документа настройки для слова](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md). В этом пошаговом руководстве представлены средства разработки Office в Visual Studio и модель программирования для настроек на уровне документа Word.  
  
 Список разделов с пошаговыми руководствами для некоторых общих задач в проектах Word см. в разделе [общие задачи программирования Office](../vsto/common-tasks-in-office-programming.md).  
  
## <a name="see-also"></a>См. также  
 [Как: Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Программирование настроек на уровне документа](../vsto/programming-document-level-customizations.md)   
 [Решения Word](../vsto/word-solutions.md)   
 [Пошаговое руководство: Создание первой настройки уровня документа для Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)   
 [Пошаговые руководства с использованием Word](../vsto/walkthroughs-using-word.md)   
 [Общие сведения об объектной модели Word](../vsto/word-object-model-overview.md)   
 [Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md)  
  
  
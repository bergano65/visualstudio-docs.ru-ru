---
title: "Пошаговое руководство: Создание шаблона с помощью элементов управления содержимым | Документы Microsoft"
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
- building blocks [Office development in Visual Studio]
- Word [Office development in Visual Studio], creating documents
- content controls [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6d221b9374bf71df3d66400289c50310263c2e9e
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-a-template-by-using-content-controls"></a>Пошаговое руководство. Создание шаблона с помощью элементов управления содержимым
  В этом пошаговом руководстве показано, как создать настройку на уровне документа, использующую элементы управления содержимым, для создания структурированного и повторно используемого содержимого в шаблоне Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Приложение Word позволяет создать коллекцию повторно используемых частей документа, с именем *стандартные блоки*. В этом пошаговом руководстве демонстрируется создание двух таблиц в качестве стандартных блоков. Каждая из них содержит несколько элементов управления, которые могут включать разные типы содержимого, например обычный текст или даты. Одна из таблиц содержит информацию о сотруднике, а другая таблица содержит отзывы.  
  
 После создания документа на основе шаблона можно добавить любую из таблиц в документ, используя несколько объектов <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl>, отображающих доступные стандартные блоки в шаблоне.  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
-   создание таблиц с элементами управления содержимым в шаблоне Word во время разработки;  
  
-   заполнение элемента управления содержимым «Поле со списком» и элемента управления содержимым «Раскрывающийся список»;  
  
-   запрет редактирования указанной таблицы пользователями;  
  
-   добавление таблиц в коллекцию стандартных блоков шаблона;  
  
-   создание элемента управления содержимым, отображающего доступные стандартные блоки в шаблоне.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Предварительные требования  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word.  
  
## <a name="creating-a-new-word-template-project"></a>Создание проекта шаблона Word  
 Создайте шаблон Word, чтобы пользователи могли легко создавать собственные копии.  
  
#### <a name="to-create-a-new-word-template-project"></a>Создание проекта шаблона Word  
  
1.  Создание проекта шаблона Word с именем **MyBuildingBlockTemplate**. В мастере создайте документ в решении. Дополнительные сведения см. в разделе [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Открывает новый шаблон Word в конструкторе и добавляет **MyBuildingBlockTemplate** проекта **обозревателе решений**.  
  
## <a name="creating-the-employee-table"></a>Создание таблицы сотрудников  
 Создайте таблицу, содержащую четыре различных типа элементов управления содержимым, в которой пользователь может ввести сведения о сотруднике.  
  
#### <a name="to-create-the-employee-table"></a>Создание таблицы сотрудников  
  
1.  В шаблоне Word, который размещен в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] на ленте щелкните **вставить** вкладки.  
  
2.  В **таблиц** щелкните **таблицы**и вставьте таблицу с двумя столбцами и четырьмя строками.  
  
3.  Введите текст в первый столбец, как показано в следующем столбце:  
  
    ||  
    |-|  
    |**Имя сотрудника**|  
    |**Дата приема на работу**|  
    |**Заголовок**|  
    |**Рисунок**|  
  
4.  Щелкните первую ячейку во втором столбце (рядом с **имя сотрудника**).  
  
5.  На ленте перейдите на вкладку **Разработчик** .  
  
    > [!NOTE]  
    >  Если вкладка **Разработчик** не отображается, сделайте ее видимой. Дополнительные сведения см. в разделе [How to: Show the Developer Tab on the Ribbon](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
6.  В **элементов управления** щелкните **текст** кнопку ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") добавление <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>в первую ячейку.  
  
7.  Щелкните вторую ячейку во втором столбце (рядом с **Дата приема на работу**).  
  
8.  В **элементов управления** щелкните **выбора даты** кнопку ![DatePickerContentControl](../vsto/media/datepicker.gif "DatePickerContentControl") добавление <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> во вторую ячейку.  
  
9. Щелкните третью ячейку во втором столбце (рядом с **заголовок**).  
  
10. В **элементов управления** щелкните **списком** кнопку ![ComboBoxContentControl](../vsto/media/combobox.gif "ComboBoxContentControl") добавление <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>в третью ячейку.  
  
11. Щелкните последнюю ячейку во втором столбце (рядом с **рисунок**).  
  
12. В **элементов управления** щелкните **элемент управления содержимым рисунка** кнопку ![PictureContentControl](../vsto/media/pictcontentcontrol.gif "PictureContentControl") для добавления <xref:Microsoft.Office.Tools.Word.PictureContentControl> в последнюю ячейку.  
  
## <a name="creating-the-customer-feedback-table"></a>Создание таблицы отзывов клиентов  
 Создайте таблицу, содержащую три различных типа элементов управления содержимым, в которой пользователь может ввести отзывы клиентов.  
  
#### <a name="to-create-the-customer-feedback-table"></a>Создание таблицы отзывов клиентов  
  
1.  В шаблоне Word щелкните строку после таблицы сотрудников, добавленной ранее, и нажмите клавишу ВВОД, чтобы добавить новый абзац.  
  
2.  На ленте щелкните **вставить** вкладки.  
  
3.  В **таблиц** щелкните **таблицы**и вставьте таблицу с двумя столбцами и тремя строками.  
  
4.  Введите текст в первый столбец, как показано в следующем столбце:  
  
    ||  
    |-|  
    |**Имя клиента**|  
    |**Степень удовлетворенности**|  
    |**Комментарии**|  
  
5.  Щелкните первую ячейку во втором столбце (рядом с **имя клиента**).  
  
6.  На ленте перейдите на вкладку **Разработчик** .  
  
7.  В **элементов управления** щелкните **текст** кнопку ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") добавление <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>в первую ячейку.  
  
8.  Щелкните вторую ячейку во втором столбце (рядом с **удовлетворенности**).  
  
9. В **элементов управления** щелкните **раскрывающегося списка** кнопку ![DropDownListContentControl](../vsto/media/dropdownlist.gif "DropDownListContentControl") для добавления <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> во вторую ячейку.  
  
10. Щелкните последнюю ячейку во втором столбце (рядом с **комментарии**).  
  
11. В **элементов управления** щелкните **форматированного текста** кнопку ![RichTextContentControl](../vsto/media/richtextcontrol.gif "RichTextContentControl") добавление <xref:Microsoft.Office.Tools.Word.RichTextContentControl>в последнюю ячейку.  
  
## <a name="populating-the-combo-box-and-drop-down-list-programmatically"></a>Заполнение поля со списком и раскрывающегося списка программным способом  
 Элементы управления содержимым можно инициализировать во время разработки с помощью **свойства** окна в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Также их можно инициализировать во время выполнения, что позволяет динамически задавать их начальное состояние. Для этого пошагового руководства используйте код для заполнения записей <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> и <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> во время выполнения, чтобы увидеть, как работают эти объекты.  
  
#### <a name="to-modify-the-ui-of-the-content-controls-programmatically"></a>Изменение пользовательского интерфейса элементов управления содержимым программным способом  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши **ThisDocument.cs** или **ThisDocument.vb**, а затем нажмите кнопку **Просмотр кода**.  
  
2.  Добавьте следующий код в класс `ThisDocument`. В этом коде объявляются несколько объектов, которые вы будете использовать позже в этом пошаговом руководстве.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#1](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#1)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#1](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#1)]  
  
3.  Добавьте в метод `ThisDocument_Startup` класса `ThisDocument` следующий код. Этот код добавляет записи в таблицы <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> и <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> и задает замещающий текст, отображаемый в каждом из этих элементов управления, прежде чем пользователь изменяет их.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#2](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#2)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#2](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#2)]  
  
## <a name="preventing-users-from-editing-the-employee-table"></a>Запрет редактирования указанной таблицы пользователями  
 Используйте объект <xref:Microsoft.Office.Tools.Word.GroupContentControl>, объявленный ранее, для защиты таблицы сотрудников. После применения защиты пользователи по-прежнему смогут редактировать элементы управления содержимым в таблице. Однако они не смогут изменять текст в первом столбце или изменять таблицу иным способом, например добавляя или удаляя строки и столбцы. Дополнительные сведения об использовании <xref:Microsoft.Office.Tools.Word.GroupContentControl> для защиты части документа см [элементы управления содержимым](../vsto/content-controls.md).  
  
#### <a name="to-prevent-users-from-editing-the-employee-table"></a>Запрет редактирования указанной таблицы пользователями  
  
1.  Добавьте следующий код в метод `ThisDocument_Startup` класса `ThisDocument` после кода, добавленного на предыдущем шаге. Этот код предотвращает изменение таблицы сотрудников, помещая таблицу внутри объекта <xref:Microsoft.Office.Tools.Word.GroupContentControl>, объявленного ранее.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#3](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#3)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#3](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#3)]  
  
## <a name="adding-the-tables-to-the-building-block-collection"></a>Добавление таблиц в коллекцию стандартных блоков  
 Добавьте таблицы в коллекцию стандартных блоков документа в шаблоне, чтобы пользователи могли вставлять таблицы, созданные вами в документе. Дополнительные сведения о стандартных блоках документа см. в разделе [элементы управления содержимым](../vsto/content-controls.md).  
  
#### <a name="to-add-the-tables-to-the-building-blocks-in-the-template"></a>Добавление таблиц в стандартные блоки в шаблоне  
  
1.  Добавьте следующий код в метод `ThisDocument_Startup` класса `ThisDocument` после кода, добавленного на предыдущем шаге. Этот код добавляет новые стандартные блоки, содержащие таблицы коллекции Microsoft.Office.Interop.Word.BuildingBlockEntries, которая содержит все повторно используемые блоки в шаблоне. Новые стандартные блоки определяются в новой категории с именем **сотрудника и информацию о клиенте** и назначается тип стандартного блока Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#4](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#4)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#4](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#4)]  
  
2.  Добавьте следующий код в метод `ThisDocument_Startup` класса `ThisDocument` после кода, добавленного на предыдущем шаге. Этот код удаляет таблицы из шаблона. Таблицы более не нужны, поскольку вы добавили их в коллекцию повторно используемых стандартных блоков в шаблоне. Код сначала переводит документ в режим конструктора, чтобы можно было удалить защищенную таблицу сотрудников.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#5](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#5)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#5](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#5)]  
  
## <a name="creating-a-content-control-that-displays-the-building-blocks"></a>Создание элемента управления содержимым, отображающего доступные стандартные блоки  
 Создайте элемент управления содержимым, предоставляющий доступ к стандартным блокам (таблицам), созданным ранее. Пользователи могут щелкнуть этот элемент управления, чтобы добавить таблицы в документ.  
  
#### <a name="to-create-a-content-control-that-displays-the-building-blocks"></a>Создание элемента управления содержимым, отображающего доступные стандартные блоки  
  
1.  Добавьте следующий код в метод `ThisDocument_Startup` класса `ThisDocument` после кода, добавленного на предыдущем шаге. Этот код инициализирует объект <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl>, объявленный ранее. <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> Отображает все стандартные блоки, которые определены в категории **сотрудника и информацию о клиенте** и имеющие тип стандартного блока Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#6](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#6)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#6](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#6)]  
  
## <a name="testing-the-project"></a>Тестирование проекта  
 Пользователи могут щелкнуть элементы управления коллекции стандартных блоков в документе, чтобы вставить таблицу сотрудников или отзывов. Пользователи могут ввести или выбрать ответы в элементах управления содержимым в обеих таблицах. Пользователи могут изменять другие части таблицы отзывов, но они не смогут менять другие части таблицы сотрудников.  
  
#### <a name="to-test-the-employee-table"></a>Проверка таблицы сотрудников  
  
1.  Нажмите клавишу F5, чтобы запустить проект.  
  
2.  Нажмите кнопку **выбрать первый стандартный блок** для отображения элемента управления первого стандартного блока.  
  
3.  Щелкните стрелку раскрывающегося списка рядом с **Настраиваемая коллекция 1** заголовка в элементе управления и выберите **таблицы Employee**.  
  
4.  Щелкните ячейку справа от **имя сотрудника** ячейку и введите имя.  
  
     Убедитесь, что в эту ячейку можно добавить только текст. <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> позволяет пользователям добавлять только текст, но не другие типы содержимого, такие как изображения или таблицы.  
  
5.  Щелкните ячейку справа от **Дата приема на работу** ячейку и выберите дату в элементе выбора даты.  
  
6.  Щелкните ячейку справа от **заголовок** ячейку и выберите один из перечисленных должностей в поле со списком.  
  
     При необходимости введите имя должности, которого нет в списке. Это возможно, поскольку <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> позволяет пользователям выбрать из списка записей или ввести собственную запись.  
  
7.  Щелкните значок в ячейке справа от **рисунок** ячейку и выберите изображение для его отображения.  
  
8.  Попробуйте добавить строки или столбцы в таблицу и попытайтесь удалить строки и столбцы из нее. Убедитесь, что изменить таблицу нельзя. <xref:Microsoft.Office.Tools.Word.GroupContentControl> не позволяет вносить какие-либо изменения.  
  
#### <a name="to-test-the-customer-feedback-table"></a>Проверка таблицы отзывов клиентов  
  
1.  Нажмите кнопку **выбрать второй стандартный блок** для отображения элемента управления второго стандартного блока.  
  
2.  Щелкните стрелку раскрывающегося списка рядом с **Настраиваемая коллекция 1** заголовка в элементе управления и выберите **таблицы Customer**.  
  
3.  Щелкните ячейку справа от **имя клиента** ячейку и введите имя.  
  
4.  Щелкните ячейку справа от **удовлетворенности** ячейку и выберите один из доступных вариантов.  
  
     Убедитесь, что нельзя вводить записи. <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> позволяет пользователям только выбирать варианты из списка элементов.  
  
5.  Щелкните ячейку справа от **комментарии** ячейку и введите несколько комментариев.  
  
     При необходимости добавьте содержимое, отличное от текста, например изображение или вложенную таблицу. Это возможно, поскольку <xref:Microsoft.Office.Tools.Word.RichTextContentControl> позволяет пользователям добавлять содержимое, отличное от текста.  
  
6.  Убедитесь, что вы можете добавить строки или столбцы в таблицу и удалить строки и столбцы из нее. Это возможно, поскольку вы не защитили таблицу, поместив ее в <xref:Microsoft.Office.Tools.Word.GroupContentControl>.  
  
7.  Закройте шаблон.  
  
## <a name="next-steps"></a>Следующие шаги  
 Дополнительные сведения об использовании элементов управления содержимым см. в следующем разделе:  
  
-   Привязка элементов управления содержимым к фрагментам XML-кода, которые также называют пользовательскими XML-частями, внедренным в документ. Дополнительные сведения см. в разделе [Пошаговое руководство: привязка элементов управления содержимым к пользовательским XML-частям](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).  
  
## <a name="see-also"></a>См. также  
 [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)   
 [Элементы управления содержимым](../vsto/content-controls.md)   
 [Как: Добавление элементов управления содержимым в документы Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Как: защита частей документов с помощью элементов управления содержимым](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)   
 [Host Items and Host Controls Overview](../vsto/host-items-and-host-controls-overview.md)   
 [Programmatic Limitations of Host Items and Host Controls](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  
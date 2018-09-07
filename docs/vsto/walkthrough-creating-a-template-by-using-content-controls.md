---
title: 'Пошаговое руководство: Создание шаблона с помощью элементов управления содержимым'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- building blocks [Office development in Visual Studio]
- Word [Office development in Visual Studio], creating documents
- content controls [Office development in Visual Studio], adding to documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 0f49e2e9e23f19a4346080b0e59435128e33849d
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "35674859"
---
# <a name="walkthrough-create-a-template-by-using-content-controls"></a>Пошаговое руководство: Создание шаблона с помощью элементов управления содержимым
  В этом пошаговом руководстве показано, как создать настройку на уровне документа, использующую элементы управления содержимым, для создания структурированного и повторно используемого содержимого в шаблоне Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Приложение Word позволяет создать коллекцию повторно используемых частей документа, с именем *стандартных блоках*. В этом пошаговом руководстве демонстрируется создание двух таблиц в качестве стандартных блоков. Каждая из них содержит несколько элементов управления, которые могут включать разные типы содержимого, например обычный текст или даты. Одна из таблиц содержит информацию о сотруднике, а другая таблица содержит отзывы.  
  
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
  
## <a name="create-a-new-word-template-project"></a>Создание нового проекта шаблона Word  
 Создайте шаблон Word, чтобы пользователи могли легко создавать собственные копии.  
  
### <a name="to-create-a-new-word-template-project"></a>Создание проекта шаблона Word  
  
1.  Создайте проект шаблона Word с именем **MyBuildingBlockTemplate**. В мастере создайте документ в решении. Дополнительные сведения см. в разделе [как: проектов Office, создайте в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Открывает новый шаблон Word в конструкторе и добавляет **MyBuildingBlockTemplate** проект **обозревателе решений**.  
  
## <a name="create-the-employee-table"></a>Создание таблицы сотрудников  
 Создайте таблицу, содержащую четыре различных типа элементов управления содержимым, в которой пользователь может ввести сведения о сотруднике.  
  
### <a name="to-create-the-employee-table"></a>Создание таблицы сотрудников  
  
1.  В шаблоне Word, который размещен в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] щелкните на ленте конструктора **вставить** вкладки.  
  
2.  В **таблиц** щелкните **таблицы**и вставьте таблицу с двумя столбцами и четырьмя строками.  
  
3.  Введите текст в первый столбец, как показано в следующем столбце:  
  
    ||  
    |-|  
    |**Имя сотрудника**|  
    |**Дата найма**|  
    |**Заголовок**|  
    |**Рисунок**|  
  
4.  Щелкните первую ячейку во втором столбце (рядом с полем **имя сотрудника**).  
  
5.  На ленте перейдите на вкладку **Разработчик** .  
  
    > [!NOTE]  
    >  Если вкладка **Разработчик** не отображается, сделайте ее видимой. Дополнительные сведения см. в разделе [как: Отображение вкладки разработчика на ленте](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
6.  В **элементов управления** щелкните **текст** кнопку ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") добавление <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>к первой ячейке.  
  
7.  Щелкните вторую ячейку во втором столбце (рядом с полем **Дата приема на работу**).  
  
8.  В **элементов управления** щелкните **Date Picker** кнопку ![DatePickerContentControl](../vsto/media/datepicker.gif "DatePickerContentControl") добавление <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> во вторую ячейку.  
  
9. Щелкните третью ячейку во втором столбце (рядом с полем **Title**).  
  
10. В **элементов управления** щелкните **поле со списком** кнопку ![ComboBoxContentControl](../vsto/media/combobox.gif "ComboBoxContentControl") добавление <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>в третью ячейку.  
  
11. Щелкните последнюю ячейку во втором столбце (рядом с полем **рисунок**).  
  
12. В **элементов управления** щелкните **элемент управления содержимым рисунка** кнопку ![PictureContentControl](../vsto/media/pictcontentcontrol.gif "PictureContentControl") для добавления <xref:Microsoft.Office.Tools.Word.PictureContentControl> в последнюю ячейку.  
  
## <a name="create-the-customer-feedback-table"></a>Создание таблицы отзывов клиентов  
 Создайте таблицу, содержащую три различных типа элементов управления содержимым, в которой пользователь может ввести отзывы клиентов.  
  
### <a name="to-create-the-customer-feedback-table"></a>Создание таблицы отзывов клиентов  
  
1.  В шаблоне Word щелкните строку после таблицы сотрудников, добавленный ранее и нажмите клавишу **ввод** для добавления нового абзаца.  
  
2.  На ленте щелкните **вставить** вкладки.  
  
3.  В **таблиц** щелкните **таблицы**и вставьте таблицу с двумя столбцами и тремя строками.  
  
4.  Введите текст в первый столбец, как показано в следующем столбце:  
  
    ||  
    |-|  
    |**Имя клиента**|  
    |**Степень удовлетворенности**|  
    |**Комментарии**|  
  
5.  Щелкните первую ячейку во втором столбце (рядом с полем **имя клиента**).  
  
6.  На ленте перейдите на вкладку **Разработчик** .  
  
7.  В **элементов управления** щелкните **текст** кнопку ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") добавление <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>к первой ячейке.  
  
8.  Щелкните вторую ячейку во втором столбце (рядом с полем **удовлетворенности**).  
  
9. В **элементов управления** щелкните **с раскрывающимся списком** кнопку ![DropDownListContentControl](../vsto/media/dropdownlist.gif "DropDownListContentControl") для добавления <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> во вторую ячейку.  
  
10. Щелкните последнюю ячейку во втором столбце (рядом с полем **комментарии**).  
  
11. В **элементов управления** щелкните **форматированный текст** кнопку ![RichTextContentControl](../vsto/media/richtextcontrol.gif "RichTextContentControl") добавление <xref:Microsoft.Office.Tools.Word.RichTextContentControl>в последнюю ячейку.  
  
## <a name="populate-the-combo-box-and-drop-down-list-programmatically"></a>Заполнить поле со списком и раскрывающегося списка программным способом  
 Элементы управления содержимым можно инициализировать во время разработки с помощью **свойства** окно в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Их также можно инициализировать во время выполнения, что позволяет динамически задавать их начальное состояние. В этом пошаговом руководстве, использовать код для заполнения записей <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> и <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> во время выполнения, которые можно видеть, как эти объекты работают.  
  
### <a name="to-modify-the-ui-of-the-content-controls-programmatically"></a>Изменение пользовательского интерфейса элементов управления содержимым программным способом  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши **ThisDocument.cs** или **ThisDocument.vb**, а затем нажмите кнопку **Просмотр кода**.  
  
2.  Добавьте следующий код в класс `ThisDocument`. В этом коде объявляются несколько объектов, которые вы будете использовать позже в этом пошаговом руководстве.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#1](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#1)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#1](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#1)]  
  
3.  Добавьте в метод `ThisDocument_Startup` класса `ThisDocument` следующий код. Этот код добавляет записи в таблицы <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> и <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> и задает замещающий текст, отображаемый в каждом из этих элементов управления, прежде чем пользователь изменяет их.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#2](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#2)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#2](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#2)]  
  
## <a name="prevent-users-from-editing-the-employee-table"></a>Запретить пользователям изменять таблицы сотрудников  
 Используйте объект <xref:Microsoft.Office.Tools.Word.GroupContentControl>, объявленный ранее, для защиты таблицы сотрудников. После применения защиты пользователи по-прежнему смогут редактировать элементы управления содержимым в таблице. Однако они не смогут изменять текст в первом столбце или изменять таблицу иным способом, например добавляя или удаляя строки и столбцы. Дополнительные сведения об использовании <xref:Microsoft.Office.Tools.Word.GroupContentControl> для защиты части документа, см. в разделе [элементы управления содержимым](../vsto/content-controls.md).  
  
### <a name="to-prevent-users-from-editing-the-employee-table"></a>Запрет редактирования указанной таблицы пользователями  
  
1.  Добавьте следующий код в метод `ThisDocument_Startup` класса `ThisDocument` после кода, добавленного на предыдущем шаге. Этот код предотвращает изменение таблицы сотрудников, помещая таблицу внутри объекта <xref:Microsoft.Office.Tools.Word.GroupContentControl>, объявленного ранее.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#3](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#3)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#3](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#3)]  
  
## <a name="add-the-tables-to-the-building-block-collection"></a>Добавление таблиц в коллекцию стандартных блоков  
 Добавьте таблицы в коллекцию стандартных блоков документа в шаблоне, чтобы пользователи могли вставлять таблицы, созданные вами в документе. Дополнительные сведения о стандартных блоках документа см. в разделе [элементы управления содержимым](../vsto/content-controls.md).  
  
### <a name="to-add-the-tables-to-the-building-blocks-in-the-template"></a>Добавление таблиц в стандартные блоки в шаблоне  
  
1.  Добавьте следующий код в метод `ThisDocument_Startup` класса `ThisDocument` после кода, добавленного на предыдущем шаге. Этот код добавляет новые стандартные блоки, содержащие таблицы коллекции Microsoft.Office.Interop.Word.BuildingBlockEntries, которая содержит все повторно используемые блоки в шаблоне. Новые стандартные блоки определяются в новую категорию с именем **сотрудников и информацию о клиенте** и назначается тип стандартного блока `Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1`.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#4](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#4)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#4](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#4)]  
  
2.  Добавьте следующий код в метод `ThisDocument_Startup` класса `ThisDocument` после кода, добавленного на предыдущем шаге. Этот код удаляет таблицы из шаблона. Таблицы более не нужны, поскольку вы добавили их в коллекцию повторно используемых стандартных блоков в шаблоне. Код сначала переводит документ в режим конструктора, чтобы можно было удалить защищенную таблицу сотрудников.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#5](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#5)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#5](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#5)]  
  
## <a name="create-a-content-control-that-displays-the-building-blocks"></a>Создание элемента управления содержимым, отображающего стандартные блоки  
 Создайте элемент управления содержимым, предоставляющий доступ к стандартным блокам (таблицам), созданным ранее. Пользователи могут щелкнуть этот элемент управления, чтобы добавить таблицы в документ.  
  
### <a name="to-create-a-content-control-that-displays-the-building-blocks"></a>Создание элемента управления содержимым, отображающего доступные стандартные блоки  
  
1.  Добавьте следующий код в метод `ThisDocument_Startup` класса `ThisDocument` после кода, добавленного на предыдущем шаге. Этот код инициализирует объект <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl>, объявленный ранее. <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> Отображает все стандартные блоки, которые определены в категории **сотрудников и информацию о клиенте** и имеющие тип стандартных блоков `Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1`.  
  
     [!code-vb[Trin_ContentControlTemplateWalkthrough#6](../vsto/codesnippet/VisualBasic/ContentControlTemplateWalkthrough/ThisDocument.vb#6)]
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#6](../vsto/codesnippet/CSharp/ContentControlTemplateWalkthrough/ThisDocument.cs#6)]  
  
## <a name="test-the-project"></a>Тестирование проекта  
 Пользователи могут щелкнуть элементы управления коллекции стандартных блоков в документе, чтобы вставить таблицу сотрудников или отзывов. Пользователи могут ввести или выбрать ответы в элементах управления содержимым в обеих таблицах. Пользователи могут изменять другие части таблицы отзывов, но они не смогут менять другие части таблицы сотрудников.  
  
### <a name="to-test-the-employee-table"></a>Проверка таблицы сотрудников  
  
1.  Нажмите клавишу **F5** для запуска проекта.  
  
2.  Нажмите кнопку **выбрать первый стандартный блок** для отображения элемента управления первый стандартный блок.  
  
3.  Щелкните стрелку раскрывающегося списка рядом с полем **Настраиваемая коллекция 1** в элементе управления и выберите **таблицы Employee**.  
  
4.  Щелкните ячейку справа от **имя сотрудника** ячейку и введите имя.  
  
     Убедитесь, что в эту ячейку можно добавить только текст. <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> позволяет пользователям добавлять только текст, но не другие типы содержимого, такие как изображения или таблицы.  
  
5.  Щелкните ячейку справа от **Дата приема на работу** ячейку и выберите дату в элементе выбора даты.  
  
6.  Щелкните ячейку справа от **Title** ячейку и выберите один из перечисленных должностей в поле со списком.  
  
     При необходимости введите имя должности, которого нет в списке. Это возможно, поскольку <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> позволяет пользователям выбрать из списка записей или ввести собственную запись.  
  
7.  Щелкните значок в ячейке справа от **рисунок** ячейку и выберите нужное изображение, чтобы отобразить ее.  
  
8.  Попробуйте добавить строки или столбцы в таблицу и попытайтесь удалить строки и столбцы из нее. Убедитесь, что изменить таблицу нельзя. <xref:Microsoft.Office.Tools.Word.GroupContentControl> не позволяет вносить какие-либо изменения.  
  
### <a name="to-test-the-customer-feedback-table"></a>Проверка таблицы отзывов клиентов  
  
1.  Нажмите кнопку **выбрать второй стандартный блок** для отображения элемента управления второй стандартный блок.  
  
2.  Щелкните стрелку раскрывающегося списка рядом с полем **Настраиваемая коллекция 1** в элементе управления и выберите **таблицы Customer**.  
  
3.  Щелкните ячейку справа от **имя клиента** ячейку и введите имя.  
  
4.  Щелкните ячейку справа от **удовлетворенности** ячейку и выберите один из доступных вариантов.  
  
     Убедитесь, что нельзя вводить записи. <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> позволяет пользователям только выбирать варианты из списка элементов.  
  
5.  Щелкните ячейку справа от **комментарии** ячейку и введите несколько комментариев.  
  
     При необходимости добавьте содержимое, отличное от текста, например изображение или вложенную таблицу. Это возможно, поскольку <xref:Microsoft.Office.Tools.Word.RichTextContentControl> позволяет пользователям добавлять содержимое, отличное от текста.  
  
6.  Убедитесь, что вы можете добавить строки или столбцы в таблицу и удалить строки и столбцы из нее. Это возможно, поскольку вы не защитили таблицу, поместив ее в <xref:Microsoft.Office.Tools.Word.GroupContentControl>.  
  
7.  Закройте шаблон.  
  
## <a name="next-steps"></a>Следующие шаги  
 Дополнительные сведения об использовании элементов управления содержимым см. в следующем разделе:  
  
-   Привязка элементов управления содержимым к фрагментам XML-кода, которые также называют пользовательскими XML-частями, внедренным в документ. Дополнительные сведения см. в разделе [Пошаговое руководство: привязать элементы управления содержимым к пользовательским XML-частям](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).  
  
## <a name="see-also"></a>См. также  
 [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)   
 [Элементы управления содержимым](../vsto/content-controls.md)   
 [Практическое: Добавление элементов управления содержимым в документы Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Практическое: защита частей документов с помощью элементов управления содержимым](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)   
 [Ведущие элементы и элементы управления](../vsto/host-items-and-host-controls-overview.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  
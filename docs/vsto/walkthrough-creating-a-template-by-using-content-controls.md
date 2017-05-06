---
title: "Пошаговое руководство. Создание шаблона с помощью элементов управления содержимым"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "стандартные блоки [разработка решений Office в Visual Studio]"
  - "элементы управления содержимым [разработка решений Office в Visual Studio], добавление к документам"
  - "Word [разработка решений Office в Visual Studio], создание документов"
ms.assetid: 88fb9a60-dcc3-4a5f-a8c9-7aff01ca4b4b
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 42
---
# Пошаговое руководство. Создание шаблона с помощью элементов управления содержимым
  В этом пошаговом руководстве показано, как создать настройку на уровне документа, использующую элементы управления содержимым, для создания структурированного и повторно используемого содержимого в шаблоне Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 Приложение Word позволяет создать коллекцию повторно используемых частей документа, которые называют *строительными блоками*.  В этом пошаговом руководстве демонстрируется создание двух таблиц в качестве стандартных блоков.  Каждая из них содержит несколько элементов управления, которые могут включать разные типы содержимого, например обычный текст или даты.  Одна из таблиц содержит информацию о сотруднике, а другая таблица содержит отзывы.  
  
 После создания документа на основе шаблона можно добавить любую из таблиц в документ, используя несколько объектов <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl>, отображающих доступные стандартные блоки в шаблоне.  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
-   создание таблиц с элементами управления содержимым в шаблоне Word во время разработки;  
  
-   заполнение элемента управления содержимым «Поле со списком» и элемента управления содержимым «Раскрывающийся список»;  
  
-   запрет редактирования указанной таблицы пользователями;  
  
-   добавление таблиц в коллекцию стандартных блоков шаблона;  
  
-   создание элемента управления содержимым, отображающего доступные стандартные блоки в шаблоне.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Обязательные компоненты  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word.  
  
## Создание проекта шаблона Word  
 Создайте шаблон Word, чтобы пользователи могли легко создавать собственные копии.  
  
#### Создание проекта шаблона Word  
  
1.  Создайте проект шаблона Word с именем MyBuildingBlockTemplate.  В мастере создайте документ в решении.  Дополнительные сведения см. в статье [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] открывает новый шаблон Word и добавляет проект **MyBuildingBlockTemplate** в **обозреватель решений**.  
  
## Создание таблицы сотрудников  
 Создайте таблицу, содержащую четыре различных типа элементов управления содержимым, в которой пользователь может ввести сведения о сотруднике.  
  
#### Создание таблицы сотрудников  
  
1.  В шаблоне Word, размещенном в конструкторе [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], на ленте выберите вкладку **Вставить**.  
  
2.  В группе **Таблицы** выберите **Таблица** и вставьте таблицу с двумя столбцами и четырьмя строками.  
  
3.  Введите текст в первый столбец, как показано в следующем столбце:  
  
    ||  
    |-|  
    |Имя сотрудника|  
    |Дата приема на работу|  
    |Заголовок|  
    |Рисунок|  
  
4.  Щелкните первую ячейку во втором столбце \(рядом с ячейкой **Имя сотрудника**\).  
  
5.  На ленте перейдите на вкладку **Разработчик**.  
  
    > [!NOTE]  
    >  Если вкладка **Разработчик** не отображается, сделайте ее видимой.  Дополнительные сведения см. в разделе [Практическое руководство. Отображение вкладки разработчика на ленте](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
6.  В группе **Элементы управления** нажмите кнопку **Текст** ![PlainTextContentControl](../vsto/media/plaintextcontrol.png "PlainTextContentControl"), чтобы добавить <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> в первую ячейку.  
  
7.  Щелкните вторую ячейку во втором столбце \(рядом с ячейкой **Дата приема на работу**\).  
  
8.  В группе **Элементы управления** нажмите кнопку **Средство выбора даты** ![DatePickerContentControl](../vsto/media/datepicker.png "DatePickerContentControl"), чтобы добавить <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> во вторую ячейку.  
  
9. Щелкните третью ячейку во втором столбце \(рядом с ячейкой **Должность**\).  
  
10. В группе **Элементы управления** нажмите кнопку **Поле со списком** ![ComboBoxContentControl](../vsto/media/combobox.png "ComboBoxContentControl"), чтобы добавить <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> в третью ячейку.  
  
11. Щелкните последнюю ячейку во втором столбце \(рядом с ячейкой **Изображение**\).  
  
12. В группе **Элементы управления** нажмите кнопку **Элемент управления содержимым рисунка** ![PictureContentControl](../vsto/media/pictcontentcontrol.png "PictureContentControl"), чтобы добавить <xref:Microsoft.Office.Tools.Word.PictureContentControl> в последнюю ячейку.  
  
## Создание таблицы отзывов клиентов  
 Создайте таблицу, содержащую три различных типа элементов управления содержимым, в которой пользователь может ввести отзывы клиентов.  
  
#### Создание таблицы отзывов клиентов  
  
1.  В шаблоне Word щелкните строку после таблицы сотрудников, добавленной ранее, и нажмите клавишу ВВОД, чтобы добавить новый абзац.  
  
2.  На ленте перейдите на вкладку **Вставка**.  
  
3.  В группе **Таблицы** выберите **Таблица** и вставьте таблицу с двумя столбцами и тремя строками.  
  
4.  Введите текст в первый столбец, как показано в следующем столбце:  
  
    ||  
    |-|  
    |Имя клиента|  
    |Степень удовлетворенности|  
    |Примечания|  
  
5.  Щелкните первую ячейку во втором столбце \(рядом с ячейкой **Имя клиента**\).  
  
6.  На ленте перейдите на вкладку **Разработчик**.  
  
7.  В группе **Элементы управления** нажмите кнопку **Текст** ![PlainTextContentControl](../vsto/media/plaintextcontrol.png "PlainTextContentControl"), чтобы добавить <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> в первую ячейку.  
  
8.  Щелкните вторую ячейку во втором столбце \(рядом с ячейкой **Степень удовлетворенности**\).  
  
9. В группе **Элементы управления** нажмите кнопку **Раскрывающийся список** ![DropDownListContentControl](../vsto/media/dropdownlist.png "DropDownListContentControl"), чтобы добавить <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> во вторую ячейку.  
  
10. Щелкните последнюю ячейку во втором столбце \(рядом с ячейкой **Комментарии**\).  
  
11. В группе **Элементы управления** нажмите кнопку **Форматированный текст** ![RichTextContentControl](../vsto/media/richtextcontrol.png "RichTextContentControl"), чтобы добавить <xref:Microsoft.Office.Tools.Word.RichTextContentControl> в последнюю ячейку.  
  
## Заполнение поля со списком и раскрывающегося списка программным способом  
 Элементы управления содержимым можно инициализировать во время разработки с помощью окна **Свойства** в [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  Также их можно инициализировать во время выполнения, что позволяет динамически задавать их начальное состояние.  В рамках этого пошагового руководства используйте код для заполнения записей <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> и <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> во время выполнения, чтобы увидеть, как эти объекты работают.  
  
#### Изменение пользовательского интерфейса элементов управления содержимым программным способом  
  
1.  В области **обозреватель решений** щелкните правой кнопкой мыши файл **ThisDocument.cs** или **ThisDocument.vb** и выберите **Просмотреть код**.  
  
2.  Добавьте следующий код в класс `ThisDocument`.  В этом коде объявляются несколько объектов, которые вы будете использовать позже в этом пошаговом руководстве.  
  
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlTemplateWalkthrough#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/VB/ThisDocument.vb#1)]  
  
3.  Добавьте в метод `ThisDocument_Startup` класса `ThisDocument` следующий код.  Этот код добавляет записи в таблицы <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> и <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> и задает замещающий текст, отображаемый в каждом из этих элементов управления, прежде чем пользователь изменяет их.  
  
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/CS/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlTemplateWalkthrough#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/VB/ThisDocument.vb#2)]  
  
## Запрет редактирования указанной таблицы пользователями  
 Используйте объект <xref:Microsoft.Office.Tools.Word.GroupContentControl>, объявленный ранее, для защиты таблицы сотрудников.  После применения защиты пользователи по\-прежнему смогут редактировать элементы управления содержимым в таблице.  Однако они не смогут изменять текст в первом столбце или изменять таблицу иным способом, например добавляя или удаляя строки и столбцы.  Дополнительные сведения об использовании <xref:Microsoft.Office.Tools.Word.GroupContentControl> для защиты части документа см. в разделе [Элементы управления содержимым](../vsto/content-controls.md).  
  
#### Запрет редактирования указанной таблицы пользователями  
  
1.  Добавьте следующий код в метод `ThisDocument_Startup` класса `ThisDocument` после кода, добавленного на предыдущем шаге.  Этот код предотвращает изменение таблицы сотрудников, помещая таблицу внутри объекта <xref:Microsoft.Office.Tools.Word.GroupContentControl>, объявленного ранее.  
  
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/CS/ThisDocument.cs#3)]
     [!code-vb[Trin_ContentControlTemplateWalkthrough#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/VB/ThisDocument.vb#3)]  
  
## Добавление таблиц в коллекцию стандартных блоков  
 Добавьте таблицы в коллекцию стандартных блоков документа в шаблоне, чтобы пользователи могли вставлять таблицы, созданные вами в документе.  Дополнительные сведения о стандартных блоках документа см. в разделе [Элементы управления содержимым](../vsto/content-controls.md).  
  
#### Добавление таблиц в стандартные блоки в шаблоне  
  
1.  Добавьте следующий код в метод `ThisDocument_Startup` класса `ThisDocument` после кода, добавленного на предыдущем шаге.  Этот код добавляет новые стандартные блоки, содержащие таблицы, в коллекцию Microsoft.Office.Interop.Word.BuildingBlockEntries, которая содержит все повторно используемые блоки в шаблоне.  Новые стандартные блоки определяются в новой категории с именем **Сведения о сотруднике и клиенте**. Им также назначается тип стандартного блока Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1.  
  
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/CS/ThisDocument.cs#4)]
     [!code-vb[Trin_ContentControlTemplateWalkthrough#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/VB/ThisDocument.vb#4)]  
  
2.  Добавьте следующий код в метод `ThisDocument_Startup` класса `ThisDocument` после кода, добавленного на предыдущем шаге.  Этот код удаляет таблицы из шаблона.  Таблицы более не нужны, поскольку вы добавили их в коллекцию повторно используемых стандартных блоков в шаблоне.  Код сначала переводит документ в режим конструктора, чтобы можно было удалить защищенную таблицу сотрудников.  
  
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/CS/ThisDocument.cs#5)]
     [!code-vb[Trin_ContentControlTemplateWalkthrough#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/VB/ThisDocument.vb#5)]  
  
## Создание элемента управления содержимым, отображающего доступные стандартные блоки  
 Создайте элемент управления содержимым, предоставляющий доступ к стандартным блокам \(таблицам\), созданным ранее.  Пользователи могут щелкнуть этот элемент управления, чтобы добавить таблицы в документ.  
  
#### Создание элемента управления содержимым, отображающего доступные стандартные блоки  
  
1.  Добавьте следующий код в метод `ThisDocument_Startup` класса `ThisDocument` после кода, добавленного на предыдущем шаге.  Этот код инициализирует объект <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl>, объявленный ранее.  <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> отображает все стандартные блоки, которые определяются в новой категории с именем **Сведения о сотруднике и клиенте** и типом стандартного блока Microsoft.Office.Interop.Word.WdBuildingBlockTypes.wdTypeCustom1.  
  
     [!code-csharp[Trin_ContentControlTemplateWalkthrough#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/CS/ThisDocument.cs#6)]
     [!code-vb[Trin_ContentControlTemplateWalkthrough#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlTemplateWalkthrough/VB/ThisDocument.vb#6)]  
  
## Тестирование проекта  
 Пользователи могут щелкнуть элементы управления коллекции стандартных блоков в документе, чтобы вставить таблицу сотрудников или отзывов.  Пользователи могут ввести или выбрать ответы в элементах управления содержимым в обеих таблицах.  Пользователи могут изменять другие части таблицы отзывов, но они не смогут менять другие части таблицы сотрудников.  
  
#### Проверка таблицы сотрудников  
  
1.  Нажмите клавишу F5, чтобы запустить проект.  
  
2.  Щелкните **Выбрать первый стандартный блок** для отображения первого элемента управления коллекции стандартных блоков.  
  
3.  Щелкните стрелку раскрывающегося списка рядом с заголовком **Настраиваемая коллекция 1** в элементе управления и выберите **Таблица Employee**.  
  
4.  Выберите ячейку справа от ячейки «Имя сотрудника» и введите имя.  
  
     Убедитесь, что в эту ячейку можно добавить только текст.  <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> позволяет пользователям добавлять только текст, но не другие типы содержимого, такие как изображения или таблицы.  
  
5.  Выберите ячейку справа от ячейки «Дата приема на работу» и выберите другую дату в элементе выбора даты.  
  
6.  Щелкните ячейку справа от ячейки «Должность» и выберите одну из перечисленных должностей в поле со списком.  
  
     При необходимости введите имя должности, которого нет в списке.  Это возможно, поскольку <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> позволяет пользователям выбрать из списка записей или ввести собственную запись.  
  
7.  Щелкните значок в ячейке справа от ячейки «Изображение» и выберите нужное изображение.  
  
8.  Попробуйте добавить строки или столбцы в таблицу и попытайтесь удалить строки и столбцы из нее.  Убедитесь, что изменить таблицу нельзя.  <xref:Microsoft.Office.Tools.Word.GroupContentControl> не позволяет вносить какие\-либо изменения.  
  
#### Проверка таблицы отзывов клиентов  
  
1.  Щелкните **Выбрать второй стандартный блок** для отображения второго элемента управления коллекции стандартных блоков.  
  
2.  Щелкните стрелку раскрывающегося списка рядом с заголовком **Настраиваемая коллекция 1** в элементе управления и выберите **Таблица Customer**.  
  
3.  Выберите ячейку справа от ячейки «Имя клиента» и введите имя.  
  
4.  Щелкните ячейку справа от ячейки «Степень удовлетворенности» и выберите один из доступных вариантов.  
  
     Убедитесь, что нельзя вводить записи.  <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> позволяет пользователям только выбирать варианты из списка элементов.  
  
5.  Выберите ячейку справа от ячейки «Комментарии» и введите несколько комментариев.  
  
     При необходимости добавьте содержимое, отличное от текста, например изображение или вложенную таблицу.  Это возможно, поскольку <xref:Microsoft.Office.Tools.Word.RichTextContentControl> позволяет пользователям добавлять содержимое, отличное от текста.  
  
6.  Убедитесь, что вы можете добавить строки или столбцы в таблицу и удалить строки и столбцы из нее.  Это возможно, поскольку вы не защитили таблицу, поместив ее в <xref:Microsoft.Office.Tools.Word.GroupContentControl>.  
  
7.  Закройте шаблон.  
  
## Следующие действия  
 Дополнительные сведения об использовании элементов управления содержимым см. в следующем разделе:  
  
-   Привязка элементов управления содержимым к фрагментам XML\-кода, которые также называют пользовательскими XML\-частями, внедренным в документ.  Дополнительные сведения см. в разделе [Пошаговое руководство. Привязка элементов управления содержимым к пользовательским XML-частям](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md).  
  
## См. также  
 [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)   
 [Элементы управления содержимым](../vsto/content-controls.md)   
 [Практическое руководство. Добавление элементов управления содержимым в документы Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Практическое руководство. Защита частей документов с помощью элементов управления содержимым](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)   
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)   
 [Программные ограничения ведущих элементов и элементов управления ведущего приложения](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Добавление элементов управления в документы Office во время выполнения](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  
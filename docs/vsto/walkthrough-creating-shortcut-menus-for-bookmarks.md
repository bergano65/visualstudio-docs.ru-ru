---
title: "Пошаговое руководство. Создание контекстного меню для закладок"
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
  - "Bookmark - элемент управления, события"
  - "контекстные меню, Word"
  - "меню, создание в приложениях Office"
  - "контекстные меню, Word"
ms.assetid: 86dbf3ff-ba75-42f9-8df6-abfc19b3cf6b
caps.latest.revision: 57
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# Пошаговое руководство. Создание контекстного меню для закладок
  Это пошаговое руководство демонстрирует, как создавать контекстные меню для элементов управления <xref:Microsoft.Office.Tools.Word.Bookmark> в настройках на уровне документа для Word.  Когда пользователь щелкает правой кнопкой мыши текст в закладке, появляется контекстное меню, содержащее параметры для форматирования текста.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
-   [Создание проекта](#BKMK_CreateProject).  
  
-   [Добавление текста и закладок в документ](#BKMK_addtextandbookmarks).  
  
-   [Добавление команды в контекстное меню](#BKMK_AddCmndsShortMenu).  
  
-   [Форматирование текста в закладке](#BKMK_formattextbkmk).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Обязательные компоненты  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] или [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]  
  
##  <a name="BKMK_CreateProject"></a> Создание проекта  
 Сначала следует создать проект документа Word в Visual Studio.  
  
#### Создание нового проекта  
  
-   Создайте проект документа Word с именем "Мое контекстное меню закладок".  Выберите в мастере **Создать новый документ**.  Для получения дополнительной информации см. [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio откроет новый документ Word в режиме конструктора и добавит проект **Мое контекстное меню закладок** в **Обозреватель решений**.  
  
##  <a name="BKMK_addtextandbookmarks"></a> Добавление текста и закладок в документ  
 Добавьте текст в документ, а затем добавьте 2 перекрывающиеся закладки.  
  
#### Добавление текста в документ  
  
-   В документе, который отображается в конструкторе проекта, введите следующий текст.  
  
     Это пример создания контекстного меню, появляющегося при щелчке правой кнопкой мыши текста закладки.  
  
#### Добавление элемента управления "Закладка" в документ  
  
1.  В **Панель элементов**, на вкладке **Элементы управления Word** и перетащите элемент управления <xref:Microsoft.Office.Tools.Word.Bookmark> в документе.  
  
     Откроется диалоговое окно **Добавление элемента управления "Закладка"**.  
  
2.  Выделите слово «создания контекстного меню, если щелкнуть правой кнопкой мыши текст», а затем щелкните **ОК**.  
  
     В документ добавляется `bookmark1`.  
  
3.  Добавьте другой элемент управления <xref:Microsoft.Office.Tools.Word.Bookmark> к ключевым словам «щелкните правой кнопкой мыши текст в закладке».  
  
     В документ добавляется `bookmark2`.  
  
    > [!NOTE]  
    >  Ключевые слова «щелкните правой кнопкой мыши текст» как `bookmark1`, так и в `bookmark2`.  
  
 При добавлении закладки к документу во время разработки создается элемент управления <xref:Microsoft.Office.Tools.Word.Bookmark>.  Можно запрограммировать несколько событий в закладке.  Можно записать код в событие <xref:Microsoft.Office.Tools.Word.Bookmark.BeforeRightClick> закладки, чтобы при нажатии пользователем правой кнопкой мыши текста в закладке появлялось контекстное меню.  
  
##  <a name="BKMK_AddCmndsShortMenu"></a> Добавление команды в контекстное меню  
 Добавьте кнопки в контекстное меню, которое открывается, если щелкнуть правой кнопкой мыши документ.  
  
#### Добавление команды в контекстное меню  
  
1.  Добавьте элемент **Элемент** в проект.  Для получения дополнительной информации см. [Практическое руководство. Работа с настройкой ленты](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
2.  В поле **Обозреватель решений** введите select **ThisDocument.cs** или **ThisDocument.vb**.  
  
3.  В строке меню выберите **Вид**, **Код**.  
  
     Файл класса **ThisDocument** будет открыт в редакторе кода.  
  
4.  Добавьте следующий код к классу **ThisDocument**.  Этот код переопределяет метод CreateRibbonExtensibilityObject и возвращает класс XML\-ленты приложению Office.  
  
     [!code-csharp[Trin_Word_Document_Menus#1](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/thisdocument.cs#1)]
     [!code-vb[Trin_Word_Document_Menus#1](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_word_document_menus/vb/thisdocument.vb#1)]  
  
5.  В **Обозреватель решений** выберите файл элемента.  По умолчанию файл имеет имя элемента Ribbon1.xml.  
  
6.  В строке меню выберите **Вид**, **Код**.  
  
     Xml\-файл ленты будет открыт в редакторе кода.  
  
7.  В редакторе кода замените содержимое файла элемента следующим кодом.  
  
    ```  
  
    <customUI xmlns="http://schemas.microsoft.com/office/2009/07/customui" onLoad="Ribbon_Load">  
      <contextMenus>  
        <contextMenu idMso="ContextMenuText">  
          <button id="BoldButton" label="Bold" onAction="ButtonClick"          
               getVisible="GetVisible" />  
          <button id="ItalicButton" label="Italic" onAction="ButtonClick"   
              getVisible="GetVisible"/>  
        </contextMenu>  
      </contextMenus>  
    </customUI>  
    ```  
  
     Этот код добавляет 2 кнопки в контекстное меню, которое открывается, если щелкнуть правой кнопкой мыши документ.  
  
8.  Правой кнопкой мыши щелкните `ThisDocument` в **Обозревателе решений**, а затем нажмите **Просмотреть код**.  
  
9. Объявите следующие переменные и переменные закладки на уровне класса.  
  
     [!code-csharp[Trin_Word_Document_Menus#2](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/thisdocument.cs#2)]
     [!code-vb[Trin_Word_Document_Menus#2](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_word_document_menus/vb/thisdocument.vb#2)]  
  
10. В **Обозреватель решений** выберите файл кода ленты.  По умолчанию файл кода ленты называется **Ribbon1.cs** или **Ribbon1.vb**.  
  
11. В строке меню выберите **Вид**, **Код**.  
  
     В редакторе кода открывается файл кода ленты.  
  
12. В файле кода ленты, добавьте следующий метод.  Это — метод обратного вызова для кнопок 2, добавленных в контекстное меню документа.  Этот метод определяет, отображаются ли эти кнопки в контекстное меню.  Полужирный курсив и кнопки отображаются только при щелчке правой кнопкой мыши текст в пределах закладки.  
  
     [!code-csharp[Trin_Word_Document_Menus#5](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/ribbon1.cs#5)]
     [!code-vb[Trin_Word_Document_Menus#5](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_word_document_menus/vb/ribbon1.vb#5)]  
  
##  <a name="BKMK_formattextbkmk"></a> Форматирование текста в закладке  
  
#### Форматирование текста в закладке  
  
1.  В файле кода ленты, добавьте обработчик событий `ButtonClick`, чтобы применить форматирование к закладке.  
  
     [!code-csharp[Trin_Word_Document_Menus#6](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/ribbon1.cs#6)]
     [!code-vb[Trin_Word_Document_Menus#6](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_word_document_menus/vb/ribbon1.vb#6)]  
  
2.  выберите **Обозреватель решений**, **ThisDocument.cs** или **ThisDocument.vb**.  
  
3.  В строке меню выберите **Вид**, **Код**.  
  
     Файл класса **ThisDocument** будет открыт в редакторе кода.  
  
4.  Добавьте следующий код к классу **ThisDocument**.  
  
     [!code-csharp[Trin_Word_Document_Menus#3](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/thisdocument.cs#3)]
     [!code-vb[Trin_Word_Document_Menus#3](../snippets/visualbasic/VS_Snippets_OfficeSP/trin_word_document_menus/vb/thisdocument.vb#3)]  
  
    > [!NOTE]  
    >  Для работы с перекрывающимися закладками необходимо записать код.   В противном случае по умолчанию код будет вызван для всех выбранных закладок.  
  
5.  В C\# также необходимо добавить обработчики событий для элементов управления закладки в событие <xref:Microsoft.Office.Tools.Word.Document.Startup>.   Дополнительные сведения о создании обработчиков событий см. в разделе [Практическое руководство. Создание обработчиков событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_Word_Document_Menus#4](../snippets/csharp/VS_Snippets_OfficeSP/trin_word_document_menus/cs/thisdocument.cs#4)]  
  
## Тестирование приложения  
 Запуск документа, чтобы убедиться, что полужирный курсив и пункты меню отображаются в контекстном меню, если щелкнуть правой кнопкой мыши текст в закладке, текст и правильно оформлен.  
  
#### Проверка документа  
  
1.  Нажмите клавишу F5 для запуска проекта.  
  
2.  Щелкните правой кнопкой мыши в первой закладке и выберите **Полужирный**.  
  
3.  Убедитесь в том, чтобы весь текст в `bookmark1` был отформатирован полужирным шрифтом.  
  
4.  Щелкните правой кнопкой мыши текст в том месте, где закладки перекрывают друг друга, и выберите **Курсив**.  
  
5.  Убедитесь в том, что курсивом отображается весь текст в `bookmark2` и только часть текста в `bookmark1`, перекрывающей `bookmark2`.  
  
## Следующие действия  
 Далее будут рассмотрены следующие задачи:  
  
-   Написание кода для реагирования на события элементов управления ведущего приложения в Excel.  Для получения дополнительной информации см. [Пошаговое руководство. Программирование реакции на события элементов управления NamedRange](../vsto/walkthrough-programming-against-events-of-a-namedrange-control.md).  
  
-   Использование флажка для изменения форматирования в закладке.  Для получения дополнительной информации см. [Пошаговое руководство. Изменение форматирования документа с использованием элементов управления CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).  
  
## См. также  
 [Пошаговые руководства с использованием Word](../vsto/walkthroughs-using-word.md)   
 [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)   
 [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)   
 [Элементы управления Bookmark](../vsto/bookmark-control.md)   
 [Необязательные параметры в решениях Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  
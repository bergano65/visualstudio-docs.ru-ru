---
title: "Пошаговое руководство. Обновление диаграммы в документе с помощью переключателей"
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
  - "элементы управления [разработка решений Office в Visual Studio], обновление документов"
  - "документы [разработка решений Office в Visual Studio], обновление с помощью элементов управления"
ms.assetid: 56e6d1f2-65a4-41f0-aff5-f0cfd96d7185
caps.latest.revision: 60
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 59
---
# Пошаговое руководство. Обновление диаграммы в документе с помощью переключателей
  В данном пошаговом руководстве описывается использование переключателей в настройке уровня документа для Microsoft Office Word, позволяющих пользователям выбирать стили диаграмм в документе.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
-   добавление диаграммы в документ проекта на уровне документа во время разработки;  
  
-   группировка переключателей путем их добавления в пользовательский элемент управления;  
  
-   изменение стиля диаграммы при выбранном параметре.  
  
 Результат в виде готового кода см. в примере элементов управления Word в разделе [Образцы и пошаговые руководства разработки Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Обязательные компоненты  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] или [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## Создание проекта  
 Первым шагом является создание документа Word.  
  
#### Создание нового проекта  
  
1.  Создайте документ Word с именем **Параметры моей диаграммы**.  Выберите в мастере элемент **Создать новый документ**.  Для получения дополнительной информации см. [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio откроет в конструкторе новый документ Word и добавит документ **Параметры моей диаграммы** в **Обозреватель решений**.  
  
## Добавление диаграммы в документ  
  
#### Добавление диаграммы  
  
1.  В документе Word, размещенном в конструкторе Visual Studio, на ленте выберите вкладку **Вставить**.  
  
2.  В группе **Текст** щелкните разворачивающуюся кнопку **Вставить объект** и выберите пункт **Объект**.  
  
     Откроется диалоговое окно **Объект**.  
  
3.  В списке **Тип объекта** на вкладке **Создать** выберите **Диаграмма Microsoft Graph** и нажмите кнопку **ОК**.  
  
     Диаграмма будет добавлена в документ в точке вставки, а затем появится окно **Таблица** с данными по умолчанию.  
  
4.  Закройте окно **Таблица**, чтобы принять в диаграмме значения по умолчанию, и щелкните внутри документа, чтобы переместить фокус от диаграммы.  
  
5.  Щелкните диаграмму правой кнопкой мыши и выберите пункт **Форматировать объект**.  
  
6.  На вкладке **Макет** диалогового окна **Форматировать объект** выберите пункт **Квадрат** и нажмите кнопку **ОК**.  
  
## Добавление пользовательского элемента управления в проект  
 Переключатели в документе не являются взаимоисключающими по умолчанию.  Их работу можно сделать правильной, добавив их в пользовательский элемент управления и написав код для управления выбором.  
  
#### Добавление пользовательского элемента управления  
  
1.  Выберите документ **Параметры моей диаграммы** в **Обозревателе решений**.  
  
2.  В меню **Проект** выберите пункт **Добавить новый элемент**.  
  
3.  В диалоговом окне **Добавить элемент** щелкните **Пользовательский элемент управления**, укажите имя элемента управления **ChartOptions** и нажмите кнопку **Добавить**.  
  
#### Добавление элементов управления формы Windows в пользовательский элемент управления  
  
1.  Если пользовательский элемент управления не отображается в конструкторе, откройте **ChartOptions** в **Обозревателе решений** двойным щелчком кнопки мыши.  
  
2.  На вкладке **Стандартные элементы управления** в области **Панель элементов** перетащите первый элемент управления **Переключатель** на пользовательский элемент управления и измените следующие свойства.  
  
    |Свойство|Значение|  
    |--------------|--------------|  
    |**Имя**|**columnChart**|  
    |**Text**|Гистограмма|  
  
3.  Добавьте второй элемент управления **Переключатель** к пользовательскому элементу управления и измените следующие свойства.  
  
    |Свойство|Значение|  
    |--------------|--------------|  
    |**Имя**|**barChart**|  
    |**Text**|Линейчатая диаграмма|  
  
4.  Добавьте третий элемент управления **Переключатель** к пользовательскому элементу управления и измените следующие свойства.  
  
    |Свойство|Значение|  
    |--------------|--------------|  
    |**Имя**|**lineChart**|  
    |**Text**|График|  
  
5.  Добавьте четвертый элемент управления **Переключатель** к пользовательскому элементу управления и измените следующие свойства.  
  
    |Свойство|Значение|  
    |--------------|--------------|  
    |**Имя**|**areaBlockChart**|  
    |**Text**|Диаграмма с областями|  
  
## Добавление ссылок  
 Чтобы получить доступ к диаграмме из пользовательского элемента управления в документе, в проекте должна присутствовать ссылка на сборку Microsoft.Office.Interop.Graph.  
  
#### Добавление ссылки на сборку Microsoft.Office.Interop.Graph  
  
1.  В меню **Проект** щелкните команду **Добавить ссылку**.  
  
     Откроется диалоговое окно **Добавление ссылки**.  
  
2.  На вкладке **.NET** выберите **Microsoft.Office.Interop.Graph** и нажмите кнопку **ОК**.  Выберите версию сборки 14.0.0.0.  
  
## Изменение стиля диаграммы при выбранном переключателе  
 Чтобы кнопки работали правильно, создайте открытое событие для пользовательского элемента управления, добавьте свойство, чтобы установить тип выбора, и создайте процедуру для события `CheckedChanged` по каждому переключателю.  
  
#### Создание события и свойства по пользовательскому элементу управления  
  
1.  В области **Обозреватель решений** щелкните правой кнопкой мыши пользовательский элемент управления и выберите пункт **Исходный текст**.  
  
2.  Добавьте код, чтобы создать событие `SelectionChanged` и свойство `Selection` в классе `ChartOptions`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#9)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ChartOptions.vb#9)]  
  
#### Обработка события переключателей CheckedChange  
  
1.  Установите тип диаграммы в обработчике событий `CheckedChanged` переключателя `areaBlockChart`, а затем породите событие.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#10)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ChartOptions.vb#10)]  
  
2.  Установите тип диаграммы в обработчик событий `CheckedChanged` переключателя `barChart`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#11)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ChartOptions.vb#11)]  
  
3.  Установите тип диаграммы в обработчик событий `CheckedChanged` переключателя `columnChart`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#12)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ChartOptions.vb#12)]  
  
4.  Установите тип диаграммы в обработчик событий `CheckedChanged` переключателя `lineChart`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#13)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ChartOptions.vb#13)]  
  
5.  В языке программирования C\# для переключателей должны быть добавлены обработчики событий.  Код можно добавить в конструктор `ChartOptions` под вызовом `InitializeComponent`.  Дополнительные сведения о создании обработчиков событий см. в разделе [Практическое руководство. Создание обработчиков событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ChartOptions.cs#14)]  
  
## Добавление пользовательского элемента управления в документ  
 При построении решения новый пользовательский элемент управления автоматически добавляется в **Панель элементов**.  Затем элемент управления можно перетащить из области **Панель элементов** в документ.  
  
#### Добавление пользовательского элемента управления в документ  
  
1.  В меню **Сборка** выберите **Собрать решение**.  
  
     Пользовательский элемент **ChartOptions** добавлен в **Панель элементов**.  
  
2.  В области **Обозреватель решений** щелкните правой кнопкой мыши файл **ThisDocument.vb** или **ThisDocument.cs** и нажмите кнопку **Конструктор представлений**.  
  
3.  Перетащите элемент управления `ChartOptions` из области **Панель элементов** в документ.  
  
     В окне **Свойства** укажите имя элемента управления, только что добавленного в документ `ChartOptions1`.  
  
## Изменение типа диаграммы  
 Создайте обработчик событий, чтобы изменить тип диаграммы в соответствии с параметром, выбранным в пользовательском элементе управления.  
  
#### Изменение типа диаграммы, отображаемой в документе  
  
1.  Добавьте следующий обработчик событий в класс `ThisDocument`.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#15)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ThisDocument.vb#15)]  
  
2.  В языке программирования C\# в событие <xref:Microsoft.Office.Tools.Word.Document.Startup> должен быть добавлен обработчик события для пользовательского элемента управления.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#16](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#16)]  
  
## Тестирование приложения  
 Теперь можно проверить документ и убедиться, что при выборе переключателя стиль диаграммы обновляется правильно.  
  
#### Проверка документа  
  
1.  Нажмите клавишу F5 для запуска проекта.  
  
2.  Выберите различные переключатели.  
  
3.  Подтвердите, что изменения стиля диаграммы соответствуют выбору.  
  
## Следующие действия  
 Ниже приводятся некоторые из возможных последующих задач.  
  
-   Использование кнопки для заполнения текстового поля.  Для получения дополнительной информации см. [Пошаговое руководство. Отображение текста в текстовом поле документа с помощью кнопки](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).  
  
-   Изменение форматирования путем выбора стиля из поля со списком.  Для получения дополнительной информации см. [Пошаговое руководство. Изменение форматирования документа с использованием элементов управления CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).  
  
## См. также  
 [Пошаговые руководства с использованием Word](../vsto/walkthroughs-using-word.md)   
 [Образцы и пошаговые руководства разработки Office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Ограничения по использованию элементов управления Windows Forms в документах Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  
---
title: "Пошаговое руководство. Отображение текста в текстовом поле документа с помощью кнопки"
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
  - "текстовые поля, отображение текста в документах"
ms.assetid: 04c54ed7-9f00-4068-aaec-1f3200110116
caps.latest.revision: 60
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 59
---
# Пошаговое руководство. Отображение текста в текстовом поле документа с помощью кнопки
  В этом пошаговом руководстве демонстрируется использование кнопок и текстовых полей в настройке уровня документа для Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
-   добавление элементов управления в документ Word в проекте на уровне документа во время разработки;  
  
-   заполнение текстового поля при нажатии кнопки.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Обязательные компоненты  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## Создание проекта  
 Первым шагом является создание документа Word.  
  
#### Создание нового проекта  
  
1.  Создайте проект документа Word с именем «Моя кнопка Word».  Выберите в мастере элемент **Создать новый документ**.  
  
     Дополнительные сведения см. в разделе [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio открывает новый документ Word в конструкторе и добавляет проект **Моя кнопка Word** в **обозреватель решений**.  
  
## Добавление элементов управления в документ Word  
 Элементы управления пользовательского интерфейса в документе Word состоят из кнопки и текстового поля.  
  
#### Добавление кнопки и текстового поля  
  
1.  Убедитесь, что документ открыт в конструкторе Visual Studio.  
  
2.  Перетащите элемент управления <xref:Microsoft.Office.Tools.Word.Controls.TextBox> со вкладки **Стандартные элементы управления** в **панели элементов** в документ.  
  
    > [!NOTE]  
    >  В Word элементы управления по умолчанию помещаются в один уровень с текстом.  Вы можете изменить способ вставки элементов управления и объектов фигур, изменив значение по умолчанию на вкладке **Правка** диалогового окна **Параметры** в приложении Word.  
  
3.  В меню **Вид** выберите пункт **Окно свойств**.  
  
4.  Найдите **TextBox1** в раскрывающемся списке окна **Свойства** и измените свойство **Имя** текстового поля на **displayText**.  
  
5.  Перетащите элемент управления **Кнопка** в документ и измените следующие свойства.  
  
    |Свойство|Значение|  
    |--------------|--------------|  
    |**Имя**|**insertText**|  
    |**Текст**|Вставить текст|  
  
 Теперь можно написать код, который будет выполняться при нажатии кнопки.  
  
## Заполнение текстового поля при нажатии кнопки  
 Каждый раз, когда пользователь нажимает кнопку, в текстовое поле добавляется строка **Hello World\!**.  
  
#### Запись в текстовое поле при нажатии кнопки  
  
1.  В **обозревателе решений** щелкните правой кнопкой мыши **ThisDocument** и выберите пункт **Просмотреть код** в контекстном меню.  
  
2.  Добавьте следующий код в обработчик событий <xref:System.Windows.Forms.Control.Click> кнопки.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ThisDocument.vb#7)]  
  
3.  В C\# необходимо добавить обработчик события кнопки в событие <xref:Microsoft.Office.Tools.Word.Document.Startup>.  Сведения о создании обработчиков событий см. в разделе [Практическое руководство. Создание обработчиков событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#8)]  
  
## Тестирование приложения  
 Теперь можно проверить документ, чтобы убедиться, что сообщение **Hello World\!** появляется в текстовом поле при нажатии кнопки.  
  
#### Проверка документа  
  
1.  Нажмите клавишу F5 для запуска проекта.  
  
2.  Нажмите кнопку.  
  
3.  Убедитесь, что сообщение **Hello World\!** появляется в текстовом поле.  
  
## Следующие действия  
 В этом пошаговом руководстве описываются основные принципы использования кнопок и текстовых полей в документах Word.  Ниже приводятся некоторые из возможных последующих задач.  
  
-   Использование поля со списком для изменения форматирования.  Дополнительные сведения см. в разделе [Пошаговое руководство. Изменение форматирования документа с использованием элементов управления CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).  
  
-   Использование переключателей для выбора стилей диаграмм.  Дополнительные сведения см. в разделе [Пошаговое руководство. Обновление диаграммы в документе с помощью переключателей](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).  
  
## См. также  
 [Общие сведения об использовании элементов управления Windows Forms в документах Office](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Пошаговые руководства с использованием Word](../vsto/walkthroughs-using-word.md)   
 [Образцы и пошаговые руководства разработки Office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Практическое руководство. Добавление элементов управления Windows Forms в документы Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)  
  
  
---
title: "Пошаговое руководство. Изменение форматирования документа с использованием элементов управления CheckBox"
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
  - "флажки, документы Word"
  - "элементы управления [разработка решений Office в Visual Studio], добавление к документам"
  - "документы [разработка решений Office в Visual Studio], элементы управления "флажок""
  - "документы [разработка решений Office в Visual Studio], форматирование"
  - "документы Word, изменение форматирования с помощью элементов управления"
ms.assetid: 3740e41d-a57e-43bb-87e7-6e5481ef290b
caps.latest.revision: 70
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 69
---
# Пошаговое руководство. Изменение форматирования документа с использованием элементов управления CheckBox
  В этом пошаговом руководстве демонстрируются принципы использования элементов управления Windows Forms для изменения форматирования текста в настройке уровня документа для Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
-   Добавление текста и элемента управления в документ в проекте уровня документа во время разработки.  
  
-   Форматирование текста при выборе параметра.  
  
 Для просмотра результатов в виде полного примера см. пример элементов управления Word в разделе [Образцы и пошаговые руководства разработки Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Обязательные компоненты  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] или [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## Создание проекта  
 Сначала следует создать проект документа Word.  
  
#### Создание нового проекта  
  
1.  Создайте проект документа Word с именем Форматирование Word.  Выберите в мастере **Создать новый документ**.  
  
     Дополнительные сведения см. в разделе [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio откроет новый документ Word в конструкторе и добавит проект **Форматирование Word** в **обозреватель решений**.  
  
## Добавление текста и элементов управления к документу Word  
 В этом пошаговом руководстве выполняется добавление трех флажков и текста в элемент управления <xref:Microsoft.Office.Tools.Word.Bookmark> в документе Word.  Флажки представляют пользователю параметры форматирования текста.  
  
#### Добавление трех флажков  
  
1.  Убедитесь, что в конструкторе Visual Studio открыт документ.  
  
2.  Перетащите в документ элемент управления <xref:Microsoft.Office.Tools.Word.Controls.CheckBox> со вкладки **Стандартные элементы управления** в **панели элементов**.  
  
3.  В окне **Свойства** измените следующие свойства:  
  
    |Свойство|Значение|  
    |--------------|--------------|  
    |**Имя**|**applyBoldFont**|  
    |**Текст.**|Полужирный|  
  
4.  Нажмите клавишу **ВВОД**, чтобы переместить точку вставки под первый флажок.  
  
5.  Добавьте в документ второй флажок под флажком `ApplyBoldFont` и измените следующие свойства:  
  
    |Свойство|Значение|  
    |--------------|--------------|  
    |**Имя**|**applyItalicFont**|  
    |**Текст.**|Курсив|  
  
6.  Нажмите клавишу **ВВОД**, чтобы переместить точку вставки под второй флажок.  
  
7.  Добавьте в документ третий флажок под флажком `ApplyItalicFont` и измените следующие свойства:  
  
    |Свойство|Значение|  
    |--------------|--------------|  
    |**Имя**|**applyUnderlineFont**|  
    |**Текст.**|Подчеркивание|  
  
#### Добавление текста и элемента управления Bookmark  
  
1.  Переместите точку вставки под флажки и введите следующий текст:  
  
     Установите соответствующий флажок, чтобы изменить форматирование текста.  
  
2.  Перетащите в документ элемент управления <xref:Microsoft.Office.Tools.Word.Bookmark> со вкладки **Элементы управления Word** в **панели элементов**.  
  
     Откроется диалоговое окно **Добавление элемента управления "Закладка"**.  
  
3.  Выделите текст, добавленный в документ, и нажмите кнопку **ОК**.  
  
     К выделенному тексту добавится элемент управления <xref:Microsoft.Office.Tools.Word.Bookmark> с именем **Bookmark1**.  
  
4.  В окне **Свойства** следует изменить значение свойства **\(Name\)** на **fontText.**  
  
 Далее следует написать код форматирования текста при установке или снятии флажка.  
  
## Форматирование текста при установке или снятии флажка  
 При выборе пользователем параметров форматирования формат текста в документе следует изменить.  
  
#### Изменение форматирования при установке флажка  
  
1.  В **обозревателе решений** щелкните правой кнопкой мыши `ThisDocument` и выберите в контекстном меню команду **Перейти к коду**.  
  
2.  Добавьте в класс **ThisDocument** следующие константы \(только в C\#\):  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#2)]  
  
3.  Добавьте следующий код к обработчику событий <xref:System.Windows.Forms.Control.Click> флажка `applyBoldFont`:  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#3)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ThisDocument.vb#3)]  
  
4.  Добавьте следующий код к обработчику событий <xref:System.Windows.Forms.Control.Click> флажка `applyItalicFont`:  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#4)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ThisDocument.vb#4)]  
  
5.  Добавьте следующий код к обработчику событий <xref:System.Windows.Forms.Control.Click> флажка `applyUnderlineFont`:  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#5)]
     [!code-vb[Trin_VstcoreProgrammingControlsWord#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/VB/ThisDocument.vb#5)]  
  
6.  В C\# также необходимо добавить обработчики событий для текстовых полей к событию <xref:Microsoft.Office.Tools.Word.Document.Startup>.  Дополнительные сведения о создании обработчиков событий см. в разделе [Практическое руководство. Создание обработчиков событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsWord/CS/ThisDocument.cs#6)]  
  
## Тестирование приложения  
 Теперь можно правильность форматирования текста документа при установке или снятии флажков.  
  
#### Проверка документа  
  
1.  Нажмите клавишу F5 для запуска проекта.  
  
2.  Установите или снимите флажок.  
  
3.  Убедитесь, что применяется правильное форматирование текста.  
  
## Следующие действия  
 В этом пошаговом руководстве описываются основы программного изменения форматирования текста в документах Word.  Далее будут рассмотрены следующие задачи:  
  
-   Заполнение текстового поля с помощью кнопки.  Дополнительные сведения см. в разделе [Пошаговое руководство. Отображение текста в текстовом поле документа с помощью кнопки](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).  
  
-   Использование переключателей для выбора стилей диаграмм.  Дополнительные сведения см. в разделе [Пошаговое руководство. Обновление диаграммы в документе с помощью переключателей](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).  
  
## См. также  
 [Пошаговые руководства с использованием Word](../vsto/walkthroughs-using-word.md)   
 [Образцы и пошаговые руководства разработки Office](../vsto/office-development-samples-and-walkthroughs.md)   
 [Элемент управления NamedRange](../vsto/namedrange-control.md)   
 [Ограничения по использованию элементов управления Windows Forms в документах Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  
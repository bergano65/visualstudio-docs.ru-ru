---
title: "Пошаговое руководство. Отображение текста в текстовом поле рабочего листа с помощью кнопки | Microsoft Docs"
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
  - "текст [разработка решений Office в Visual Studio], отображение листов"
  - "текст [разработка решений Office в Visual Studio], текстовые поля"
  - "текстовые поля, отображение текста в листах"
  - "листы, отображение текста"
ms.assetid: 59b73159-aab7-4f61-9ace-1723c18d78d6
caps.latest.revision: 56
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 55
---
# Пошаговое руководство. Отображение текста в текстовом поле рабочего листа с помощью кнопки
  В этом пошаговом руководстве описываются основные принципы использования кнопок и текстовых полей на рабочих листах Microsoft Office Excel и способы создания проектов Excel с помощью средств разработки Office в Visual Studio.  Для просмотра результатов в готовом примере обратитесь к примеру элементов управления Excel в разделе [Образцы и пошаговые руководства разработки Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 В процессе выполнения этого пошагового руководства вы научитесь:  
  
-   добавление элементов управления на лист;  
  
-   заполнение текстового поля при нажатии кнопки;  
  
-   Тестирование проекта.  
  
> [!NOTE]  
>  Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях.  Эти элементы определяются используемым выпуском Visual Studio и его параметрами.  Дополнительные сведения см. в разделе [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ru-ru/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Обязательные компоненты  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] или [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## Создание проекта  
 На данном этапе с помощью Visual Studio создается проект книги Excel.  
  
#### Создание нового проекта  
  
1.  Создайте проект книги Excel с именем Кнопка Excel.  Убедитесь, что выбрано **Создать новый документ**.  Дополнительные сведения см. в разделе [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Созданная книга Excel открывается в конструкторе Visual Studio, и проект **Кнопка Excel** добавляется в **Обозреватель решений**.  
  
## Добавление элементов управления на лист  
 Для этого пошагового руководства требуется кнопка и текстовое поле на первом листе.  
  
#### Добавление кнопки и текстового поля  
  
1.  Убедитесь, что книга **Мои Excel Button.xlsx** открыта в конструкторе Visual Studio, и `Sheet1`.  
  
2.  С вкладки **Стандартные элементы управления** панели элементов перетащите элемент управления <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> на лист `Sheet1`.  
  
3.  В меню **Вид** выберите команду **Окно свойств**.  
  
4.  Убедитесь, что элемент **TextBox1** отображается в раскрывающемся списке окна **Свойства**, и присвойте его свойству **Name** значение **displayText**.  
  
5.  Перетащите элемент управления **Кнопка** на лист `Sheet1` и измените следующие свойства:  
  
    |Свойство|Значение|  
    |--------------|--------------|  
    |**Имя**|**insertText**|  
    |**Текст.**|Вставить текст|  
  
 Теперь напишите код, выполняемый при нажатии кнопки.  
  
## Заполнение текстового поля при нажатии кнопки  
 Каждый раз, когда пользователь нажимает кнопку **Здравствуй, мир\!** добавляется в текстовое поле.  
  
#### Добавление текста в текстовое поле при нажатии кнопки  
  
1.  В **обозревателе решений** щелкните правой кнопкой мыши **Sheet1** и выберите в контекстном меню команду **Просмотреть код**.  
  
2.  В обработчик событий <xref:System.Windows.Forms.Control.Click> кнопки добавьте следующий код:  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/VB/Sheet1.vb#11)]  
  
3.  В C\# необходимо добавлять обработчик событий <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>, как показано ниже.  Сведения о создании обработчиков событий см. в разделе [Практическое руководство. Создание обработчиков событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgrammingControlsExcel/CS/Sheet1.cs#12)]  
  
## Тестирование приложения  
 Теперь тест в книгу, чтобы убедиться, что сообщение в текстовое поле **Здравствуй, мир\!**. при нажатии кнопки.  
  
#### Проверка рабочей книги  
  
1.  Нажмите клавишу F5 для запуска проекта.  
  
2.  Щелкните кнопку.  
  
3.  Убедитесь, что в текстовом поле отображается текст **Здравствуй, мир\!**.  
  
## Следующие действия  
 В этом пошаговом руководстве рассмотрены основные принципы использования кнопок и текстовых полей на рабочих листах Excel.  Далее будут рассмотрены следующие задачи:  
  
-   Развертывание проекта.  Дополнительные сведения см. в разделе [Развертывание решения Office](../vsto/deploying-an-office-solution.md).  
  
-   Использование флажков для изменения форматирования.  Дополнительные сведения см. в разделе [Пошаговое руководство. Изменение форматирования листа с использованием элементов управления CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).  
  
## См. также  
 [Практическое руководство. Добавление элементов управления Windows Forms в документы Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Пошаговые руководства с использованием Excel](../vsto/walkthroughs-using-excel.md)   
 [Ограничения по использованию элементов управления Windows Forms в документах Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  
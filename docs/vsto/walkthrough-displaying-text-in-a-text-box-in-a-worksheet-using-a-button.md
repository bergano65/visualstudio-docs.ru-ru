---
title: "Пошаговое руководство: Отображение текста в текстовом поле на листе с помощью кнопки | Документы Microsoft"
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
- text [Office development in Visual Studio], displaying worksheets
- worksheets, displaying text
- text boxes, displaying text in worksheets
- text [Office development in Visual Studio], text boxes
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 7b88940aa1329bc330e5d8bb7d114c21fac3dacb
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button"></a>Пошаговое руководство. Отображение текста в текстовом поле рабочего листа с помощью кнопки
  В этом пошаговом руководстве описываются основные принципы использования кнопок и текстовых полей на листах Microsoft Office Excel и способы создания проектов Excel, с помощью средств разработки Office в Visual Studio. Для просмотра результатов в виде полного примера, см [примеры разработки решений Office и пошаговые руководства](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
 В этом пошаговом руководстве описаны следующие процедуры.  
  
-   Добавление элементов управления на лист.  
  
-   Заполнение текстового поля при нажатии кнопки.  
  
-   Тестирование проекта.  
  
> [!NOTE]  
>  Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Предварительные требования  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] или [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].  
  
## <a name="creating-the-project"></a>Создание проекта  
 На этом шаге вы создадите проект книги Excel с помощью Visual Studio.  
  
#### <a name="to-create-a-new-project"></a>Создание нового проекта  
  
1.  Создайте проект книги Excel с именем **кнопка Excel**. Убедитесь, что **создания документа** выбран. Дополнительные сведения см. в разделе [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio открывает новую книгу Excel в конструкторе и добавляет **кнопка Excel** проекта **обозревателе решений**.  
  
## <a name="adding-controls-to-the-worksheet"></a>Добавление элементов управления на лист  
 В этом пошаговом руководстве необходимо будет кнопку и текстовое поле на первый лист.  
  
#### <a name="to-add-a-button-and-a-text-box"></a>Добавление кнопки и текстового поля  
  
1.  Убедитесь, что **Мои Button.xlsx Excel** книга открыта в конструкторе Visual Studio с `Sheet1` отображается.  
  
2.  Из **стандартные элементы управления** вкладки панели элементов перетащите <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> для `Sheet1`.  
  
3.  Из **представление** последовательно выберите пункты **окно свойств**.  
  
4.  Убедитесь, что **TextBox1** является видимым в **свойства** окно раскрывающегося списка и измените **имя** свойства текстового поля, чтобы **displayText**.  
  
5.  Перетащите **кнопку** управления `Sheet1` и измените следующие свойства:  
  
    |Свойство.|Значение|  
    |--------------|-----------|  
    |**Name**|**insertText**|  
    |**Text**|**Вставка текста**|  
  
 Теперь можно напишите код, выполняемый при нажатии кнопки.  
  
## <a name="populating-the-text-box-when-the-button-is-clicked"></a>Заполнение текстового поля при нажатии кнопки  
 При каждом нажатии кнопки, **Здравствуй, мир!** добавляется в текстовое поле.  
  
#### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Запись в текстовое поле при нажатии кнопки  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши **Sheet1**, а затем нажмите кнопку **Просмотр кода** в контекстном меню.  
  
2.  Добавьте следующий код в <xref:System.Windows.Forms.Control.Click> обработчика событий кнопки:  
  
     [!code-vb[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#11)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#11)]  
  
3.  В C# необходимо добавить обработчик событий для <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> события, как показано ниже. Сведения о создании обработчиков событий см. в разделе [как: Создание обработчиков событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#12)]  
  
## <a name="testing-the-application"></a>Тестирование приложения  
 Теперь можно проверить книги, чтобы убедиться, что сообщение **Здравствуй, мир!** отображается в текстовом поле при нажатии кнопки.  
  
#### <a name="to-test-your-workbook"></a>Проверка книги  
  
1.  Нажмите клавишу F5 для запуска проекта.  
  
2.  Нажмите кнопку.  
  
3.  Убедитесь, что **Hello World!** отображается в текстовом поле.  
  
## <a name="next-steps"></a>Следующие шаги  
 В этом пошаговом руководстве описываются основные принципы использования кнопок и текстовых полей на листах Excel. Ниже приводятся некоторые из возможных последующих задач.  
  
-   Развертывание проекта. Дополнительные сведения см. в разделе [развертывание решения Office](../vsto/deploying-an-office-solution.md).  
  
-   С помощью флажков для изменения форматирования. Дополнительные сведения см. в разделе [Пошаговое руководство: изменение листа форматирования с помощью элементов управления CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).  
  
## <a name="see-also"></a>См. также  
 [Как: Добавление элементов управления в документы Office Windows Forms](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Пошаговые руководства с использованием Excel](../vsto/walkthroughs-using-excel.md)   
 [Ограничения по использованию элементов управления Windows Forms в документах Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  
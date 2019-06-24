---
title: Отображаемый текст в текстовом поле в лист с помощью кнопки
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], displaying worksheets
- worksheets, displaying text
- text boxes, displaying text in worksheets
- text [Office development in Visual Studio], text boxes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b30eea0152b75cdd0869ececac674ee5aeee7933
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/22/2019
ms.locfileid: "67328708"
---
# <a name="walkthrough-display-text-in-a-text-box-in-a-worksheet-using-a-button"></a>Пошаговое руководство. Отображаемый текст в текстовом поле на листе с помощью кнопки
  В этом пошаговом руководстве описываются основные принципы использования кнопок и текстовых полей на листах Microsoft Office Excel и созданию проектов Excel, с помощью средств разработки Office в Visual Studio. Чтобы просмотреть результат в виде готового кода, см [примеры разработки решений Office и пошаговые руководства](../vsto/office-development-samples-and-walkthroughs.md).

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 В этом пошаговом руководстве описаны следующие процедуры.

- Добавление элементов управления на лист.

- Заполнение текстового поля при нажатии кнопки.

- Тестирование проекта.

> [!NOTE]
> Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Предварительные требования
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] или [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

## <a name="create-the-project"></a>Создание проекта
 На этом шаге вы создадите проект книги Excel с помощью Visual Studio.

### <a name="to-create-a-new-project"></a>Создание нового проекта

1. Создайте проект книги Excel с именем **кнопка Excel**. Убедитесь, что **создания документа** выбран. Дополнительные сведения см. в разделе [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio открывает новую книгу Excel в конструкторе и добавляет **кнопка Excel** проект **обозревателе решений**.

## <a name="add-controls-to-the-worksheet"></a>Добавление элементов управления на лист
 В этом пошаговом руководстве потребуется кнопку и текстовое поле на первом листе.

### <a name="to-add-a-button-and-a-text-box"></a>Добавление кнопки и текстового поля

1. Убедитесь, что **Мои Button.xlsx Excel** книга открыта в конструкторе Visual Studio с `Sheet1` отображается.

2. Из **стандартные элементы управления** вкладки панели элементов перетащите <xref:Microsoft.Office.Tools.Excel.Controls.TextBox> для `Sheet1`.

3. Из **представление** меню, выберите **окно "Свойства"** .

4. Убедитесь, что **TextBox1** является видимым в **свойства** "раскрывающегося списка" окна "и измените **имя** свойства текстового поля значение **displayText**.

5. Перетащите **кнопку** управления `Sheet1` и измените следующие свойства:

   |Свойство|Значение|
   |--------------|-----------|
   |**Name**|**insertText**|
   |**Text**|**Вставить текст**|

   Теперь можно напишите код для выполнения при нажатии кнопки.

## <a name="populate-the-text-box-when-the-button-is-clicked"></a>Заполнение текстового поля при нажатии кнопки
 Каждый раз, пользователь нажимает кнопку, **Hello World!** добавляется в текстовое поле.

### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Запись в текстовое поле при нажатии кнопки

1. В **обозревателе решений**, щелкните правой кнопкой мыши **Sheet1**, а затем нажмите кнопку **просмотреть код** в контекстном меню.

2. Добавьте следующий код, чтобы <xref:System.Windows.Forms.Control.Click> обработчик событий кнопки:

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#11)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#11)]

3. В C# необходимо добавить обработчик событий к <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> событий, как показано ниже. Сведения о создании обработчиков событий см. в разделе [как: Создание обработчиков событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#12](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#12)]

## <a name="test-the-application"></a>Тестирование приложения
 Теперь можно протестировать книги, чтобы убедиться, что сообщение **Hello World!** отображается в текстовом поле при нажатии кнопки.

### <a name="to-test-your-workbook"></a>Проверка книги

1. Нажмите клавишу **F5** для запуска проекта.

2. Нажмите кнопку.

3. Убедитесь, что **Hello World!** отображается в текстовом поле.

## <a name="next-steps"></a>Следующие шаги
 В этом пошаговом руководстве описываются основные принципы использования кнопок и текстовых полей на листах Excel. Ниже приводятся некоторые из возможных последующих задач.

- Развертывание проекта. Дополнительные сведения см. в разделе [развертывание решения Office](../vsto/deploying-an-office-solution.md).

- С помощью флажков для изменения форматирования. Дополнительные сведения см. в разделе [Пошаговое руководство: Изменение форматирования листа с использованием элементов управления CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md).

## <a name="see-also"></a>См. также
- [Практическое руководство. Добавление элементов управления Windows Forms в документы Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Пошаговые руководства с помощью Excel](../vsto/walkthroughs-using-excel.md)
- [Ограничения элементов управления Windows Forms в документах Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)

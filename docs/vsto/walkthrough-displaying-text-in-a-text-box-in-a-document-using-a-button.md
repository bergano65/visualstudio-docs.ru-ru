---
title: "Пошаговое руководство: Отображение текста в текстовом поле документа с помощью кнопки | Документы Microsoft"
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
helpviewer_keywords: text boxes, displaying text in documents
ms.assetid: 04c54ed7-9f00-4068-aaec-1f3200110116
caps.latest.revision: "60"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 75146e583f2b15557a2f88ba18ed5d8798c7603b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button"></a>Пошаговое руководство. Отображение текста в текстовом поле документа с помощью кнопки
  В этом пошаговом руководстве демонстрируется использование кнопок и текстовых полей в настройке уровня документа для Microsoft Office Word.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
-   добавление элементов управления в документ Word в проекте на уровне документа во время разработки;  
  
-   заполнение текстового поля при нажатии кнопки.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Предварительные требования  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## <a name="creating-the-project"></a>Создание проекта  
 Первым шагом является создание документа Word.  
  
#### <a name="to-create-a-new-project"></a>Создание нового проекта  
  
1.  Создайте проект документа Word с именем **Моя кнопка Word**. В мастере выберите **создания документа**.  
  
     Дополнительные сведения см. в разделе [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio откроет новый документ Word в конструкторе и добавляет **Моя кнопка Word** проекта **обозревателе решений**.  
  
## <a name="adding-controls-to-the-word-document"></a>Добавление элементов управления в документ Word  
 Элементы управления пользовательского интерфейса в документе Word состоят из кнопки и текстового поля.  
  
#### <a name="to-add-a-button-and-a-text-box"></a>Добавление кнопки и текстового поля  
  
1.  Убедитесь, что документ открыт в конструкторе Visual Studio.  
  
2.  Из **стандартные элементы управления** вкладке **элементов**, перетащите <xref:Microsoft.Office.Tools.Word.Controls.TextBox> элемента управления в документ.  
  
    > [!NOTE]  
    >  В Word элементы управления по умолчанию сбрасываются в один уровень с текстом. Вы можете изменить элементов управления и объектов фигур вставляются, изменив значение по умолчанию на **изменить** вкладке **параметры** диалоговое окно в Word.  
  
3.  В меню **Вид** выберите пункт **Окно свойств**.  
  
4.  Найти **TextBox1** в **свойства** окно раскрывающегося списка и измените **имя** свойства текстового поля, чтобы **displayText**.  
  
5.  Перетащите **кнопку** управления в документ и измените следующие свойства.  
  
    |Свойство|Значение|  
    |--------------|-----------|  
    |**Имя**|**insertText**|  
    |**Text**|**Вставка текста**|  
  
 Теперь можно написать код, который будет выполняться при нажатии кнопки.  
  
## <a name="populating-the-text-box-when-the-button-is-clicked"></a>Заполнение текстового поля при нажатии кнопки  
 Каждый раз, когда пользователь нажимает кнопку, **Здравствуй, мир!** добавляется в текстовое поле.  
  
#### <a name="to-write-to-the-text-box-when-the-button-is-clicked"></a>Запись в текстовое поле при нажатии кнопки  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши **ThisDocument**, а затем нажмите кнопку **Просмотр кода** в контекстном меню.  
  
2.  Добавьте следующий код в обработчик событий <xref:System.Windows.Forms.Control.Click> кнопки.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#7)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#7](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#7)]  
  
3.  В C# необходимо добавить обработчик события кнопки в событие <xref:Microsoft.Office.Tools.Word.Document.Startup>. Сведения о создании обработчиков событий см. в разделе [как: Создание обработчиков событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#8](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#8)]  
  
## <a name="testing-the-application"></a>Тестирование приложения  
 Теперь можно проверить документ, чтобы убедиться, что сообщение **Здравствуй, мир!** отображается в текстовом поле при нажатии кнопки.  
  
#### <a name="to-test-your-document"></a>Проверка документа  
  
1.  Нажмите клавишу F5 для запуска проекта.  
  
2.  Нажмите кнопку.  
  
3.  Убедитесь, что **Hello World!** отображается в текстовом поле.  
  
## <a name="next-steps"></a>Дальнейшие действия  
 В этом пошаговом руководстве описываются основные принципы использования кнопок и текстовых полей в документах Word. Ниже приводятся некоторые из возможных последующих задач.  
  
-   Использование поля со списком для изменения форматирования. Дополнительные сведения см. в разделе [Пошаговое руководство: изменение документов форматирования с помощью элементов управления CheckBox](../vsto/walkthrough-changing-document-formatting-using-checkbox-controls.md).  
  
-   Использование переключателей для выбора стилей диаграмм. Дополнительные сведения см. в разделе [Пошаговое руководство: обновление диаграммы в документе с помощью переключателей](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).  
  
## <a name="see-also"></a>См. также  
 [Элементы управления в документах Office Windows Forms](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Пошаговые руководства с использованием Word](../vsto/walkthroughs-using-word.md)   
 [Примеры разработки решений Office и пошаговые руководства](../vsto/office-development-samples-and-walkthroughs.md)   
 [Как: Добавление элементов управления в документы Office Windows Forms](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)   
 [Общие сведения о ведущих элементах и элементах управления ведущего приложения](../vsto/host-items-and-host-controls-overview.md)  
  
  
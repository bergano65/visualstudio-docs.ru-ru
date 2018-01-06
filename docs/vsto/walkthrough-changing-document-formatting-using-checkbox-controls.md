---
title: "Пошаговое руководство: Изменение форматирования документа с использованием элементов управления CheckBox | Документы Microsoft"
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
- Word documents, changing formatting using controls
- documents [Office development in Visual Studio], formatting
- check boxes, Word documents
- documents [Office development in Visual Studio], check box controls
- controls [Office development in Visual Studio], adding to documents
ms.assetid: 3740e41d-a57e-43bb-87e7-6e5481ef290b
caps.latest.revision: "70"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: a0c8d44c32c03f98a0d2621eff3899ded101b7d3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-changing-document-formatting-using-checkbox-controls"></a>Пошаговое руководство. Изменение форматирования документа с использованием элементов управления CheckBox
  В этом пошаговом руководстве демонстрируется использование элементов управления Windows Forms в настройке уровня документа для Microsoft Office Word для изменения форматирования текста.  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
-   Добавление текста и элемента управления в документ в проекте уровня документа во время разработки.  
  
-   Форматирование текста при выбранном параметре.  
  
 Для просмотра результатов в виде полного примера, см [примеры разработки решений Office и пошаговые руководства](../vsto/office-development-samples-and-walkthroughs.md).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Предварительные требования  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] или [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## <a name="creating-the-project"></a>Создание проекта  
 Первым шагом является создание документа Word.  
  
#### <a name="to-create-a-new-project"></a>Создание нового проекта  
  
1.  Создайте проект документа Word с именем **форматирование Word**. В мастере выберите **создания документа**.  
  
     Дополнительные сведения см. в разделе [How to: Create Office Projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio откроет новый документ Word в конструкторе и добавляет **форматирование Word** проекта **обозревателе решений**.  
  
## <a name="adding-text-and-controls-to-the-word-document"></a>Добавление текста и элементов управления в документ Word  
 В этом пошаговом руководстве, добавьте три флажка и некоторый текст в <xref:Microsoft.Office.Tools.Word.Bookmark> элемента управления в документ Word. Флажки представляют параметры пользователя для форматирования текста.  
  
#### <a name="to-add-three-check-boxes"></a>Чтобы добавить три флажка  
  
1.  Убедитесь, что документ открыт в конструкторе Visual Studio.  
  
2.  Из **стандартные элементы управления** вкладке **элементов**, перетащите первый <xref:Microsoft.Office.Tools.Word.Controls.CheckBox> элемента управления в документ.  
  
3.  В окне **Свойства** измените следующие свойства.  
  
    |Свойство.|Значение|  
    |--------------|-----------|  
    |**Name**|**applyBoldFont**|  
    |**Text**|**Полужирный**|  
  
4.  Нажмите клавишу **ввод** переместить точку вставки под первый флажок.  
  
5.  Добавьте второй флажок в документ ниже `ApplyBoldFont` и измените следующие свойства.  
  
    |Свойство.|Значение|  
    |--------------|-----------|  
    |**Name**|**applyItalicFont**|  
    |**Text**|**Курсив**|  
  
6.  Нажмите клавишу **ввод** переместить точку вставки под второй флажок.  
  
7.  Добавьте третий флажок в документ ниже `ApplyItalicFont` и измените следующие свойства.  
  
    |Свойство.|Значение|  
    |--------------|-----------|  
    |**Name**|**applyUnderlineFont**|  
    |**Text**|**Подчеркивание**|  
  
#### <a name="to-add-text-and-a-bookmark-control"></a>Добавление текста и элемента управления Bookmark  
  
1.  Поместите курсор ниже управления «флажок» и введите следующий текст:  
  
     **Установите флажок, чтобы изменить форматирование текста.**  
  
2.  Из **элементы управления Word** вкладке **элементов**, перетащите <xref:Microsoft.Office.Tools.Word.Bookmark> элемента управления в документ.  
  
     **Добавление элемента управления Bookmark** откроется диалоговое окно.  
  
3.  Выберите текст, добавленный в документ и нажмите кнопку **ОК**.  
  
     Объект <xref:Microsoft.Office.Tools.Word.Bookmark> управления с именем **Bookmark1** добавляется к тексту, выбранному в документе.  
  
4.  В **свойства** окна, измените значение **(имя)** свойства **fontText.**  
  
 Затем напишите код для форматирования текста, когда этот флажок установлен или снят флажок.  
  
## <a name="formatting-the-text-when-a-check-box-is-checked-or-cleared"></a>Форматирование текста при флажка — при установке или снятии  
 Когда пользователь выбирает способ форматирования, измените формат текста в документе.  
  
#### <a name="to-change-formatting-when-a-check-box-is-selected"></a>Для изменения форматирования, если флажок установлен  
  
1.  Щелкните правой кнопкой мыши `ThisDocument` в **обозревателе решений**, а затем нажмите кнопку **Просмотр кода** в контекстном меню.  
  
2.  Только в C#, добавьте следующие константы для **ThisDocument** класса.  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#2](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#2)]  
  
3.  Добавьте следующий код в <xref:System.Windows.Forms.Control.Click> обработчик событий `applyBoldFont` флажок.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#3)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#3](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#3)]  
  
4.  Добавьте следующий код в <xref:System.Windows.Forms.Control.Click> обработчик событий `applyItalicFont` флажок.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#4)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#4](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#4)]  
  
5.  Добавьте следующий код в <xref:System.Windows.Forms.Control.Click> обработчик событий `applyUnderlineFont` флажок.  
  
     [!code-vb[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/VisualBasic/my chart options/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#5)]  
  
6.  В C# необходимо добавить обработчики событий для текстовых полей к <xref:Microsoft.Office.Tools.Word.Document.Startup> событий. Сведения о создании обработчиков событий см. в разделе [как: Создание обработчиков событий в проектах Office](../vsto/how-to-create-event-handlers-in-office-projects.md).  
  
     [!code-csharp[Trin_VstcoreProgrammingControlsWord#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsWordCS/ThisDocument.cs#6)]  
  
## <a name="testing-the-application"></a>Тестирование приложения  
 Теперь можно проверить документ, чтобы убедиться, что текст имеет правильный формат при установке или снятии флажка.  
  
#### <a name="to-test-your-document"></a>Проверка документа  
  
1.  Нажмите клавишу F5 для запуска проекта.  
  
2.  Установите или снимите флажок.  
  
3.  Убедитесь, что текст имеет правильный формат.  
  
## <a name="next-steps"></a>Следующие шаги  
 В этом пошаговом руководстве показаны основные принципы использования флажков и программное изменение форматирования текста в документах Word. Ниже приводятся некоторые из возможных последующих задач.  
  
-   Использование кнопки для заполнения текстового поля. Дополнительные сведения см. в разделе [Пошаговое руководство: отображение текста в текстовом поле в документ с помощью кнопки](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-document-using-a-button.md).  
  
-   Использование переключателей для выбора стилей диаграмм. Дополнительные сведения см. в разделе [Пошаговое руководство: обновление диаграммы в документе с помощью переключателей](../vsto/walkthrough-updating-a-chart-in-a-document-using-radio-buttons.md).  
  
-  
  
## <a name="see-also"></a>См. также  
 [Пошаговые руководства с использованием Word](../vsto/walkthroughs-using-word.md)   
 [Примеры разработки решений Office и пошаговые руководства](../vsto/office-development-samples-and-walkthroughs.md)   
 [Элемент управления NamedRange](../vsto/namedrange-control.md)   
 [Ограничения по использованию элементов управления Windows Forms в документах Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)  
  
  
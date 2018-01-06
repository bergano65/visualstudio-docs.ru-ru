---
title: "Специальные возможности в проектах Office | Документы Microsoft"
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
- Office development in Visual Studio, accessibility
- shortcut keys [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], shortcut keys
- accessibility [Office development in Visual Studio]
ms.assetid: 48efcf1f-ca49-47ce-99f0-cc99f051aeae
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 01ef94199ae7ea22f72ca08be4dfb9092b03403f
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="accessibility-in-office-projects"></a>Специальные возможности в проектах Office
  Microsoft Visual Studio и Microsoft Office содержат многие специальные возможности, которые позволяют создавать пользовательские решения, отвечающие требованиям стандартных специальных возможностей. Корпорация Майкрософт публикует рекомендации по специальным возможностям в Интернете. Дополнительные сведения см. в разделе [специальных возможностей веб-сайт](http://go.microsoft.com/fwlink/?LinkID=37113).  
  
 В большинстве случаев проекты Office в Visual Studio соответствуют стандартам и предоставляют свойства специальных возможностей, задаваемых в отношении. Однако существуют некоторые функции, которые имеют ограниченный доступ.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## <a name="accessibility-at-design-time"></a>Специальные возможности во время разработки  
  
### <a name="using-shortcut-keys-in-document-level-projects"></a>Использование сочетаний клавиш в проектах уровня документа  
 Когда документ Microsoft Office Word или книге Microsoft Office Excel открыто в Visual Studio, только одно приложение получает сочетания клавиш. По умолчанию Visual Studio получает сочетания клавиш, но можно сделать Word или Excel, для их получения, если документ имеет фокус, выбрав **Динамическая схема клавиатуры** на **параметры клавиатуры** страницы из **параметры** диалоговое окно. Дополнительные сведения см. в разделе [Microsoft Office Word клавиатуре параметры клавиатуры Microsoft Office, параметры](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md) и [Microsoft Office Excel Keyboard, настройки клавиатуры Microsoft Office, параметры](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md).  
  
### <a name="displaying-shortcut-keys-for-the-ribbon-in-document-level-projects"></a>Отображение сочетаний клавиш для ленты в проектах уровня документа  
 Когда документ Word или книги Excel открыто в Visual Studio, сочетания клавиш для вкладок и элементов управления на ленте не отображаются при нажатии клавиши Alt. Чтобы просмотреть сочетания клавиш, пока документ или книгу в конструкторе, выполните следующие действия.  
  
##### <a name="to-view-shortcut-keys-for-ribbon-tabs-and-controls-in-the-designer"></a>Чтобы просмотреть сочетания клавиш для вкладок и элементов ленты в конструкторе  
  
1.  В Visual Studio на **средства** меню, нажмите кнопку **параметры**.  
  
2.  Разверните **средств Office** , а затем установите **Microsoft Office Excel клавиатуры** или **Microsoft Office Word клавиатуры**соответствующим образом.  
  
3.  Выберите **Динамическая схема клавиатуры**.  
  
     Появится сообщение о том, что необходимо перезапустить Visual Studio, чтобы изменения вступили в силу.  
  
4.  Нажмите кнопку **ОК**.  
  
5.  Перезапустите Visual Studio и повторно откройте проект.  
  
6.  Откройте документ или книгу, конструктор проекта.  
  
7.  Нажмите клавишу F6, чтобы отобразить сочетания клавиш для ленты.  
  
## <a name="accessibility-at-run-time"></a>Специальные возможности во время выполнения  
  
### <a name="windows-forms-controls-on-office-documents"></a>Элементы управления в документах Office Windows Forms  
 Элементы управления Windows Forms предоставляют свойства специальных возможностей для предоставления сведений об элементе управления для доступа к специальным возможностям, такие как средства чтения с экрана. Вы сможете использовать эти свойства, когда элементы управления находятся в документ Office в настройке на уровне документа. Дополнительные сведения см. в разделе [предоставляет сведения о специальных возможностях для элементов управления в форме Windows](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form).  
  
 Однако существуют некоторые ограничения специальных возможностей во время выполнения, при вложении элементов управления Windows Forms в книге Excel или документе Word:  
  
-   Нельзя осуществлять переход от одного элемента управления на другой.  
  
-   Элементов управления в документе отключаются при изменении значения масштабирования документа на отличное от 100%.  
  
 Сведения об ограничениях элементов управления Windows Forms в документы см. в разделе [ограничения для элементов управления Windows Forms в документах Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).  
  
### <a name="actions-panes-and-custom-task-panes"></a>Панели действий и настраиваемые области задач  
 Когда панель действий или настраиваемой области задач в фокусе, доступ к элементам управления так же, как и к элементам управления в приложении Windows Forms. Для перемещения курсора между областью действия и документа, можно нажать клавишу **F6**.  
  
 Дополнительные сведения о панели действий и настраиваемые области задач см. в разделе [Общие сведения о панели действий](../vsto/actions-pane-overview.md) и [настраиваемые области задач](../vsto/custom-task-panes.md).  
  
### <a name="display-modes"></a>Режимы отображения  
 Visual Studio имеет следующие ограничения, связанные с режимами отображения:  
  
-   Элементы управления в документе Word или листа Excel отключены при изменении значения масштабирования документа на отличное от 100%.  
  
-   **Новый проект** диалоговое окно отображаться элементы управления неправильно, если пользователь изменяет параметры специальных возможностей компьютера, чтобы **Высокая контрастность**.  
  
 Экранная лупа позволяет устранить эти ограничения. Экранная лупа является служебной программой отображения в Windows, которая создает отдельный окно, отображающее увеличенная часть экрана.  
  
## <a name="see-also"></a>См. также  
 [Разработка решений Office](../vsto/developing-office-solutions.md)   
 [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)   
 [Специальные возможности для людей с ограниченными возможностями](/visualstudio/ide/reference/accessibility-for-people-with-disabilities)   
 [Специальные возможности Visual Studio](/visualstudio/ide/reference/accessibility-features-of-visual-studio)  
  
  
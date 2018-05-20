---
title: Специальные возможности в проектах Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, accessibility
- shortcut keys [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], shortcut keys
- accessibility [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 34a1ea090e85168b5fd0bf2e55c22d0a38ff331f
ms.sourcegitcommit: 209c2c068ff0975994ed892b62aa9b834a7f6077
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/17/2018
---
# <a name="accessibility-in-office-projects"></a>Специальные возможности в проектах Office
  Microsoft Visual Studio и Microsoft Office содержат многие специальные возможности, которые позволяют создавать пользовательские решения, отвечающие требованиям стандартных специальных возможностей. Корпорация Майкрософт публикует рекомендации по специальным возможностям в Интернете. Дополнительные сведения см. в разделе [веб-сайте специальных возможностей](http://go.microsoft.com/fwlink/?LinkID=37113).  

 В большинстве случаев проекты Office в Visual Studio соответствуют стандартам и предоставляют свойства специальных возможностей, задаваемых в отношении. Однако существуют некоторые функции, которые имеют ограниченный доступ.  

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  

## <a name="accessibility-at-design-time"></a>Специальные возможности во время разработки  

### <a name="use-shortcut-keys-in-document-level-projects"></a>Использование сочетаний клавиш в проектах уровня документа  
 Когда документ Microsoft Office Word или книге Microsoft Office Excel открыто в Visual Studio, только одно приложение получает сочетания клавиш. По умолчанию Visual Studio получает сочетания клавиш, но можно сделать Word или Excel, для их получения, если документ имеет фокус, выбрав **Динамическая схема клавиатуры** на **параметры клавиатуры** страницы из **параметры** диалоговое окно. Дополнительные сведения см. в разделе [Microsoft Office Word клавиатуры, параметры клавиатуры Microsoft Office, диалоговое окно «Параметры»](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md) и [Microsoft Office Excel клавиатуры, параметры клавиатуры Microsoft Office, диалоговое окно «Параметры»](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md).  

### <a name="display-shortcut-keys-for-the-ribbon-in-document-level-projects"></a>Отображать сочетания клавиш для ленты в проектах уровня документа  
 Когда документ Word или книги Excel открыто в Visual Studio, не отображаются при нажатии **Alt** раздел, чтобы просмотреть сочетания клавиш для вкладок и элементов управления на ленте. Чтобы просмотреть сочетания клавиш, пока документ или книгу в конструкторе, выполните следующие действия.  

#### <a name="to-view-shortcut-keys-for-ribbon-tabs-and-controls-in-the-designer"></a>Чтобы просмотреть сочетания клавиш для вкладок и элементов ленты в конструкторе  

1.  В Visual Studio на **средства** меню, нажмите кнопку **параметры**.  

2.  Разверните **средств Office** , а затем установите **Microsoft Office Excel клавиатуры** или **Microsoft Office Word клавиатуры**соответствующим образом.  

3.  Выберите **Динамическая схема клавиатуры**.  

     Появится сообщение о том, что необходимо перезапустить Visual Studio, чтобы изменения вступили в силу.  

4.  Нажмите кнопку **ОК**.  

5.  Перезапустите Visual Studio и повторно откройте проект.  

6.  Откройте документ или книгу, конструктор проекта.  

7.  Нажмите клавишу **F6** для отображения сочетания клавиш для ленты.  

## <a name="accessibility-at-runtime"></a>Специальные возможности во время выполнения  

### <a name="windows-forms-controls-on-office-documents"></a>Элементы управления Windows Forms в документах Office  
 Элементы управления Windows Forms предоставляют свойства специальных возможностей для предоставления сведений об элементе управления для доступа к специальным возможностям, такие как средства чтения с экрана. Вы сможете использовать эти свойства, когда элементы управления находятся в документ Office в настройке на уровне документа. Дополнительные сведения см. в разделе [предоставляют сведения о специальных возможностях для элементов управления в форме Windows](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form).  

 Однако существуют некоторые ограничения специальных возможностей во время выполнения, когда элементы управления Windows Forms, размещаются в книге Excel или документе Word:  

-   Нельзя осуществлять переход от одного элемента управления на другой.  

-   Элементов управления в документе отключаются при изменении значения масштабирования документа на отличное от 100%.  

 Сведения об ограничениях элементов управления Windows Forms в документы см. в разделе [управляет ограничения Windows Forms в документах Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).  

### <a name="actions-panes-and-custom-task-panes"></a>Панели действий и настраиваемые области задач  
 Когда панель действий или настраиваемой области задач в фокусе, доступ к элементам управления так же, как и к элементам управления в приложении Windows Forms. Для перемещения курсора между областью действия и документа, можно нажать клавишу **F6**.  

 Дополнительные сведения о панели действий и настраиваемые области задач см. в разделе [Общие сведения о панели действий](../vsto/actions-pane-overview.md) и [настраиваемых панелей задач](../vsto/custom-task-panes.md).  

### <a name="display-modes"></a>Режимы отображения  
 Visual Studio имеет следующие ограничения, связанные с режимами отображения:  

-   Элементы управления в документе Word или листа Excel отключены при изменении значения масштабирования документа на отличное от 100%.  

-   **Новый проект** диалоговое окно отображаться элементы управления неправильно, если пользователь изменяет параметры специальных возможностей компьютера, чтобы **Высокая контрастность**.  

 Экранная лупа позволяет устранить эти ограничения. Экранная лупа является служебной программой отображения в Windows, которая создает отдельный окно, отображающее увеличенная часть экрана.  

## <a name="see-also"></a>См. также  
 [Разработки решений Office](../vsto/developing-office-solutions.md)   
 [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)   
 [Специальные возможности для людей с ограниченными возможностями](/visualstudio/ide/reference/accessibility-for-people-with-disabilities)   
 [Специальные возможности Visual Studio](/visualstudio/ide/reference/accessibility-features-of-visual-studio)  

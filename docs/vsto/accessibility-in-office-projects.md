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
ms.openlocfilehash: e7d056d8f5cb014d48827faf0ec10a8a23bd8d03
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49938829"
---
# <a name="accessibility-in-office-projects"></a>Специальные возможности в проектах Office
  Microsoft Visual Studio и Microsoft Office включают множество функций специальных возможностей, которые позволяют создавать собственные решения, которые соответствуют требованиям стандартных специальных возможностей. Корпорация Майкрософт публикует рекомендации для объекта специальных возможностей в Интернете. Дополнительные сведения см. в разделе [веб-сайте специальных возможностей](http://go.microsoft.com/fwlink/?LinkID=37113).  

 В большинстве случаев проекты Office в Visual Studio соответствует стандартам и предоставляют свойства специальных возможностей, которые можно задать в отношении. Однако существуют некоторые функции, которые имеют ограниченный специальных возможностей.  

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  

## <a name="accessibility-at-design-time"></a>Специальные возможности во время разработки  

### <a name="use-shortcut-keys-in-document-level-projects"></a>Использование сочетаний клавиш в проектах уровня документа  
 При открытии в Visual Studio в документ Microsoft Office Word или книге Microsoft Office Excel только одно приложение за раз получает сочетания клавиш. По умолчанию Visual Studio получает нажатие сочетания клавиш, но можно сделать Word или Excel, для их получения, если документ имеет фокус, выбрав **Инамическая схема клавиатуры** на **параметры клавиатуры** страницы из **параметры** диалоговое окно. Дополнительные сведения см. в разделе [Microsoft Office Word клавиатуры, параметры клавиатуры Microsoft Office, диалоговое окно "Параметры"](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md) и [Microsoft Office Excel клавиатуры, параметры клавиатуры Microsoft Office, диалоговое окно "Параметры"](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md).  

### <a name="display-shortcut-keys-for-the-ribbon-in-document-level-projects"></a>Отображать сочетания клавиш для ленты в проектах уровня документа  
 При открытии в Visual Studio документ Word или книги Excel не удается нажать клавишу **Alt** клавишу, чтобы просмотреть сочетания клавиш для вкладок и элементов управления на ленте. Чтобы просмотреть сочетания клавиш, пока в конструкторе открыт документ или книгу, выполните следующие действия.  

#### <a name="to-view-shortcut-keys-for-ribbon-tabs-and-controls-in-the-designer"></a>Чтобы просмотреть сочетания клавиш для вкладок и элементов ленты в конструкторе  

1.  В Visual Studio на **средства** меню, щелкните **параметры**.  

2.  Разверните **средств Office** узел и выберите **Microsoft Office Excel клавиатуры** или **Microsoft Office Word клавиатуры**, соответствующим образом.  

3.  Выберите **Инамическая схема клавиатуры**.  

     Появится сообщение о том, что необходимо перезапустить Visual Studio, чтобы изменения вступили в силу.  

4.  Нажмите кнопку **ОК**.  

5.  Перезапустите Visual Studio и повторно откройте проект.  

6.  Откройте конструктор документ или книгу для вашего проекта.  

7.  Нажмите клавишу **F6** для отображения сочетания клавиш для ленты.  

## <a name="accessibility-at-runtime"></a>Специальные возможности во время выполнения  

### <a name="windows-forms-controls-on-office-documents"></a>Элементы управления Windows Forms в документах Office  
 Элементы управления Windows Forms предоставляют свойства специальных возможностей для предоставления сведений об элементе управления, для вспомогательных средств, таких как средства чтения с экрана. Можно воспользоваться преимуществами эти свойства, когда элементы управления находятся в документ Office, в настройке уровня документа. Дополнительные сведения см. в разделе [предоставляют сведения о специальных возможностях для элементов управления в форме Windows](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form).  

 Тем не менее существуют некоторые ограничения доступности во время выполнения, когда элементы управления Windows Forms размещаются на книги Excel или документе Word:  

- Нельзя осуществлять переход от одного элемента управления на другой.  

- Элементов управления в документе будут отключены, если изменить настройку масштаба документа только на 100%.  

  Сведения об ограничениях элементов управления Windows Forms в документах, см. в разделе [управляет ограничения Windows Forms в документах Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).  

### <a name="actions-panes-and-custom-task-panes"></a>Панели действий и настраиваемые области задач  
 Когда панель действий или настраиваемой области задач имеет фокус, доступ к элементам управления так же, доступ к элементам управления в приложении Windows Forms. Для перемещения курсора между областью действия и документа, можно нажать клавишу **F6**.  

 Дополнительные сведения о панели действий и настраиваемые области задач, см. в разделе [Общие сведения о панели действий](../vsto/actions-pane-overview.md) и [настраиваемых панелей задач](../vsto/custom-task-panes.md).  

### <a name="display-modes"></a>Режимы отображения  
 Visual Studio имеет следующие ограничения, связанные с режимами отображения:  

- Элементы управления в документ Word или листе Excel будут отключены при изменении значения масштабирования документа на отличное от 100%.  

- **Новый проект** диалоговое окно отображается элементы управления неправильно, если пользователь изменяет параметры специальных возможностей компьютера, чтобы **Высокая контрастность**.  

  Экранная лупа можно использовать для преодоления этих ограничений. Экранная лупа является служебной программой отображения в Windows, создающий плавающими, отображающий увеличенная часть экрана.  

## <a name="see-also"></a>См. также  
 [Разработка решений Office](../vsto/developing-office-solutions.md)   
 [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)   
 [Специальные возможности для людей с ограниченными возможностями](/visualstudio/ide/reference/accessibility-for-people-with-disabilities)   
 [Специальные возможности Visual Studio](/visualstudio/ide/reference/accessibility-features-of-visual-studio)  

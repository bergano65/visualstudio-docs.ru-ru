---
title: Специальные возможности в проектах Office
description: Узнайте, как Microsoft Office проекты включают множество специальных возможностей, позволяющих создавать пользовательские решения, соответствующие стандартным требованиям специальных возможностей.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, accessibility
- shortcut keys [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], shortcut keys
- accessibility [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4021517aa296f3c1e6355b82260b00590181f4cb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955155"
---
# <a name="accessibility-in-office-projects"></a>Специальные возможности в проектах Office

Microsoft Visual Studio и Microsoft Office включают множество специальных возможностей, позволяющих создавать пользовательские решения, соответствующие стандартным требованиям специальных возможностей. Корпорация Майкрософт публикует рекомендации по специальным возможностям в Интернете. Дополнительные сведения см. на [веб-сайте Accessibility](https://www.microsoft.com/accessibility/).

В большинстве случаев проекты Office в Visual Studio соответствуют стандартам специальных возможностей или предоставляют свойства, которые можно настроить, чтобы сделать ваши решения доступными. Однако некоторые функции имеют ограниченный доступ.

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="accessibility-at-design-time"></a>Специальные возможности во время разработки

### <a name="use-shortcut-keys-in-document-level-projects"></a>Использование сочетаний клавиш в проектах уровня документа
 Если документ Word Microsoft Office или книга Microsoft Office Excel открыты в Visual Studio, то только одно приложение за раз получит команды сочетания клавиш. По умолчанию Visual Studio получает все сочетания клавиш, но вы можете сделать Word или Excel получать их, если фокус находится на документе, выбрав пункт **Динамическая схема клавиатуры** на странице **Параметры клавиатуры** диалогового окна **Параметры** . Дополнительные сведения см. в разделе [Microsoft Office Word Keyboard, Microsoft Office параметры клавиатуры, диалоговое окно Параметры](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md) и [Microsoft Office клавиатура Excel, Microsoft Office параметры клавиатуры, диалоговое окно Параметры](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md).

### <a name="display-shortcut-keys-for-the-ribbon-in-document-level-projects"></a>Отображение сочетаний клавиш для ленты в проектах уровня документа
 Если документ Word или книга Excel открыты в Visual Studio, нельзя нажать клавишу **ALT** , чтобы просмотреть сочетания клавиш для вкладок и элементов управления на ленте. Чтобы просмотреть сочетания клавиш во время открытия документа или книги в конструкторе, выполните следующие действия.

#### <a name="to-view-shortcut-keys-for-ribbon-tabs-and-controls-in-the-designer"></a>Просмотр сочетаний клавиш для вкладок и элементов управления ленты в конструкторе

1. В Visual Studio в меню **Сервис** выберите пункт **Параметры**.

2. Разверните узел **средства Office** и выберите **Microsoft Officeную клавиатуру Excel** или **Microsoft Office Word**, в зависимости от ситуации.

3. Выберите **Динамическая схема клавиатуры**.

     Появится сообщение о том, что необходимо перезапустить Visual Studio, чтобы изменения вступили в силу.

4. Нажмите кнопку **OK**.

5. Перезапустите Visual Studio и снова откройте проект.

6. Откройте в проекте конструктор документов или книг.

7. Нажмите клавишу **F6** , чтобы отобразить сочетания клавиш для ленты.

## <a name="accessibility-at-run-time"></a>Специальные возможности во время выполнения

### <a name="windows-forms-controls-on-office-documents"></a>Windows Forms элементов управления в документах Office
 Windows Forms элементы управления предоставляют свойства специальных возможностей для предоставления сведений об элементе управления специальным средствам, таким как средства чтения с экрана. Можно воспользоваться преимуществами этих свойств специальных возможностей, если элементы управления находятся в документе Office в настройке на уровне документа. Дополнительные сведения см. [в разделе Предоставление сведений о специальных возможностях для элементов управления в Windows Forms](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form).

 Однако существуют некоторые ограничения специальных возможностей во время выполнения, когда Windows Forms элементы управления размещаются в книге Excel или документе Word:

- Нельзя выполнить переход от одного элемента управления к другому.

- Элементы управления в документе отключаются при изменении параметра масштаба документа на что-либо, кроме 100%.

  Сведения об ограничениях элементов управления Windows Forms в документах см. в разделе [ограничения элементов управления Windows Forms в документах Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).

### <a name="actions-panes-and-custom-task-panes"></a>Панели действий и настраиваемые области задач
 Если фокус находится на панели действий или настраиваемой области задач, доступ к элементам управления осуществляется так же, как и к элементам управления в Windows Forms приложении. Чтобы переместить курсор между панелью действий и документом, можно нажать клавишу **F6**.

 Дополнительные сведения о панелях действий и настраиваемых панелях задач см. в разделе [Общие сведения о панели действий](../vsto/actions-pane-overview.md) и [пользовательские области задач](../vsto/custom-task-panes.md).

### <a name="display-modes"></a>Режимы отображения

Visual Studio имеет следующие ограничения, связанные с режимами отображения:

- Элементы управления в документе Word или листе Excel отключаются при изменении параметра масштаба документа на что-либо, кроме 100%.

- Диалоговое окно **Новый проект** неправильно отображает элементы управления, если пользователь изменяет параметры специальных возможностей компьютера для **использования высокая контрастность**.

Для преодоления этих ограничений можно использовать экранную лупу. Экранная лупа — это программа отображения в Windows, которая создает отдельное окно, в котором отображается увеличенная часть экрана.

## <a name="see-also"></a>См. также раздел

- [Разработка решений Office](../vsto/developing-office-solutions.md)
- [Элементы управления в документах Office](../vsto/controls-on-office-documents.md)
- [Специальные возможности для людей с ограниченными возможностями](../ide/reference/accessibility-features-of-visual-studio.md)
- [Специальные возможности Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md)
---
title: Разработка приложений Windows Forms
ms.date: 08/09/2019
ms.topic: conceptual
helpviewer_keywords:
- Windows Forms Designer
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b26ad18da19d5a2e53199b49e7acc024c728be9c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72634030"
---
# <a name="windows-forms-designer-overview"></a>Обзор конструктора Windows Forms

Конструктор Windows Forms в Visual Studio — это решение для быстрого создания приложений на основе Windows Forms. Конструктор Windows Forms позволяет легко добавлять элементы управления в форму, упорядочивать их и писать код для их событий. Дополнительные сведения о Windows Forms см. в [обзорной статье об этом решении](/dotnet/framework/winforms/windows-forms-overview).

## <a name="functionality"></a>Функция

Конструктор позволяет выполнять такие задачи:

- Добавлять в форму компоненты, элементы управления данными или элементы управления для Windows.

- Дважды щелкнув форму в конструкторе, создавать код в событии `Load` этой формы или, дважды щелкнув элемент управления в форме, создавать код для события по умолчанию этого элемента управления.

- Изменять свойство Text элемента управления, выбрав элемент управления и введя имя.

- Изменять положение выбранного элемента управления, перемещая его с помощью мыши или клавиш со стрелками. Таким же образом задавать точное положение элемента с помощью клавиши CTRL и клавиш со стрелками. Наконец, изменять размер элемента управления с помощью клавиши SHIFT и клавиш со стрелками.

- Одновременно выбирать несколько элементов управления, нажимая клавишу **SHIFT** или **CTRL** при щелчке. Если использовать клавишу **SHIFT** в сочетании со щелчком, первый выбранный элемент управления становится главным при выравнивании или изменении размера. Если использовать клавишу **CTRL** в сочетании со щелчком, главным становится последний выбранный элемент, поэтому главный элемент управления меняется при добавлении нового элемента. Кроме того, можно выбрать несколько элементов управления, очертив требуемые элементы управления прямоугольником выделения.

> [!NOTE]
> Для внесения изменений в файл ресурсов формы (*RESX*) используйте конструктор Windows Forms, а не редактор ресурсов. При редактировании файла RESX, связанного с формой, отображается предупреждение о том, что изменения, внесенные в редакторе ресурсов, могут быть потеряны. Это происходит потому, что конструктор Windows Forms создает файл RESX.

## <a name="see-also"></a>См. также

- [Windows Forms overview](/dotnet/framework/winforms/windows-forms-overview) (Общие сведения о Windows Forms)
- [Элементы управления Windows Forms](/dotnet/framework/winforms/controls/)
- [User input in Windows Forms](/dotnet/framework/winforms/user-input-in-windows-forms) (Ввод данных пользователем в Windows Forms)
- [Data binding in Windows Forms](/dotnet/framework/winforms/windows-forms-data-binding) (Привязка данных Windows Forms)
- [Enhance Windows Forms apps](/dotnet/framework/winforms/advanced/) (Усовершенствование приложений Windows Forms)
- Справочник по API <xref:System.Windows.Forms?displayProperty=fullName>
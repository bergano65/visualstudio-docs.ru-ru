---
title: Разработка приложений Windows Forms
description: Сведения о конструкторе Windows Forms в Visual Studio, который предоставляет собой решение для быстрого создания приложений на основе Windows Forms.
ms.custom: SEO-VS-2020
ms.date: 08/09/2019
ms.topic: overview
helpviewer_keywords:
- Windows Forms Designer
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: 768c19f78102bf19346867beda967a069c1d182e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844961"
---
# <a name="windows-forms-designer-overview"></a>Обзор конструктора Windows Forms

Конструктор Windows Forms в Visual Studio — это решение для быстрого создания приложений на основе Windows Forms. Конструктор Windows Forms позволяет легко добавлять элементы управления в форму, упорядочивать их и писать код для их событий. Дополнительные сведения о Windows Forms см. в [обзорной статье об этом решении](/dotnet/framework/winforms/windows-forms-overview).

## <a name="functionality"></a>функциональное назначение;

Конструктор позволяет выполнять такие задачи:

- Добавлять в форму компоненты, элементы управления данными или элементы управления для Windows.

- Дважды щелкнув форму в конструкторе, создавать код в событии `Load` этой формы или, дважды щелкнув элемент управления в форме, создавать код для события по умолчанию этого элемента управления.

- Изменять свойство Text элемента управления, выбрав элемент управления и введя имя.

- Изменять положение выбранного элемента управления, перемещая его с помощью мыши или клавиш со стрелками. Таким же образом задавать точное положение элемента с помощью клавиши CTRL и клавиш со стрелками. Наконец, изменять размер элемента управления с помощью клавиши SHIFT и клавиш со стрелками.

- Одновременно выбирать несколько элементов управления, нажимая клавишу **SHIFT** или **CTRL** при щелчке. Если использовать клавишу **SHIFT** в сочетании со щелчком, первый выбранный элемент управления становится главным при выравнивании или изменении размера. Если использовать клавишу **CTRL** в сочетании со щелчком, главным становится последний выбранный элемент, поэтому главный элемент управления меняется при добавлении нового элемента. Кроме того, можно выбрать несколько элементов управления, очертив требуемые элементы управления прямоугольником выделения.

> [!NOTE]
> Для внесения изменений в файл ресурсов формы (*RESX*) используйте конструктор Windows Forms, а не редактор ресурсов. При редактировании файла RESX, связанного с формой, отображается предупреждение о том, что изменения, внесенные в редакторе ресурсов, могут быть потеряны. Это происходит потому, что конструктор Windows Forms создает файл RESX.

## <a name="see-also"></a>См. также раздел

- [Windows Forms overview](/dotnet/framework/winforms/windows-forms-overview) (Общие сведения о Windows Forms)
- [Элементы управления Windows Forms](/dotnet/framework/winforms/controls/)
- [User input in Windows Forms](/dotnet/framework/winforms/user-input-in-windows-forms) (Ввод данных пользователем в Windows Forms)
- [Data binding in Windows Forms](/dotnet/framework/winforms/windows-forms-data-binding) (Привязка данных Windows Forms)
- [Enhance Windows Forms apps](/dotnet/framework/winforms/advanced/) (Усовершенствование приложений Windows Forms)
- Справочник по API <xref:System.Windows.Forms?displayProperty=fullName>

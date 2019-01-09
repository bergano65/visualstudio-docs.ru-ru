---
title: Привязка элементов управления к рисункам из базы данных
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- images [Visual Basic], displaying on Windows Forms
- data binding [Windows Forms], pictures
- images [Visual Basic], data binding
- pictures, data binding
- pictures, dragging from Data Sources window
- Data Sources Window, setting controls to display images
- PictureBox control [Windows Forms], data binding
- images [Visual Basic], dragging from Data Sources window
ms.assetid: 9748815e-3556-49e8-86b1-c6aa593c6163
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 803de097d05f472e7a5b585a8b58395c45a924ed
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: ru-RU
ms.lasthandoff: 01/02/2019
ms.locfileid: "53914998"
---
# <a name="bind-controls-to-pictures-from-a-database"></a>Привязка элементов управления к рисункам из базы данных

Можно использовать **источников данных** окно для привязки изображения в базе данных к элементу управления в приложении. Например, можно привязать к изображению <xref:System.Windows.Controls.Image> управления в приложении WPF или <xref:System.Windows.Forms.PictureBox> элемента управления в приложении Windows Forms.

Изображения в базе данных обычно хранятся в виде байтовых массивов. Элементы в **источников данных** окно, в котором хранятся в виде байтовых массивов имеют управления введите значение **None** по умолчанию, поскольку массивы байтов может содержать что угодно — от простого массива байтов до исполняемого файла большого приложения. Создание элемента управления с привязкой к данным для элемента массива байтов в **источников данных** окно, которое представляет изображение, необходимо выбрать элемент управления для создания.

Следующая процедура предполагает, что **источников данных** уже заполняется элементами, связанными с изображением.

## <a name="to-bind-a-picture-in-a-database-to-a-control"></a>Чтобы привязать изображение в базе данных к элементу управления

1.  Убедитесь, что, в область конструктора, который вы хотите добавить элемент управления был открыт в конструкторе WPF или в конструкторе Windows Forms.

2.  В **источников данных** окне разверните нужную таблицу или объект для отображения его свойств или столбцов.

   > [!TIP]
   > Если **источников данных** окно не открыто, откройте его, выбрав **представление** > **Other Windows** > **источников данных**.

3.  Выберите столбец или свойство, которое содержит данные изображения и выберите один из следующих элементов управления из его управляющий элемент раскрывающегося списка:

    - Если открыт конструктор WPF, выберите **изображение**.

    - Если открыт конструктор Windows Forms, выберите **PictureBox**.

    - Кроме того можно выбрать другой элемент управления, который поддерживает привязку данных и может отображать изображения. Если элемент управления, который вы хотите использовать не в списке доступных элементов управления, можно добавить его в список и выберите ее. Дополнительные сведения см. в разделе [добавлять пользовательские элементы управления окна "Источники данных"](../data-tools/add-custom-controls-to-the-data-sources-window.md).

## <a name="see-also"></a>См. также

- [Привязка элементов управления WPF к данным в Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
---
title: Привязка элементов управления к рисункам из базы данных | Документы Microsoft
ms.custom: ''
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
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 29d902f16051bd04079115baf87e33ac49d77396
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="bind-controls-to-pictures-from-a-database"></a>Привязка элементов управления к рисункам из базы данных
Можно использовать **источники данных** окна для привязки изображения в базе данных к элементу управления в приложении. Например, можно привязать к изображению <xref:System.Windows.Controls.Image> управления в приложении WPF или <xref:System.Windows.Forms.PictureBox> элемента управления в приложении Windows Forms.  
  
Изображения в базе данных обычно хранятся в виде байтовых массивов. Элементы в **источники данных** окно, в котором хранятся в виде массивов байтов управлять их введите значение **нет** по умолчанию, так как байтовые массивы могут содержать что угодно — от простого массива байтов до исполняемого файла большого приложения. Создание элемента управления с привязкой к данным для элемента массива байтов в **источники данных** окно, которое представляет изображение, необходимо выбрать элемент управления для создания.  
  
В следующей процедуре предполагается, что **источники данных** уже заполняется элементами, связанными с изображением. 
  
### <a name="to-bind-a-picture-in-a-database-to-a-control"></a>Чтобы привязать изображение в базе данных к элементу управления  
  
1.  Убедитесь в том, что необходимо добавить элемент управления в рабочей области конструирования открыт в конструкторе WPF или конструктор Windows Forms.  
  
2.  В **источники данных** окна, разверните нужную таблицу или объект для отображения его свойств или столбцов.  
  
3.  Выберите столбец или свойство, содержащее данные изображения и выберите один из следующих элементов управления из своего управляющий элемент раскрывающегося списка:  
  
    -   Если открыт конструктор WPF, выберите **изображения**.  
  
    -   Если открыт конструктор Windows Forms, выберите **PictureBox**.  
  
    -   Кроме того можно выбрать другой элемент управления, который поддерживает привязку данных и может отображать изображения. Если элемент управления, который вы хотите использовать не находится в списке доступных элементов управления, можно добавить в список и выберите его. Дополнительные сведения см. в разделе [добавить пользовательские элементы управления в окно источников данных](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
## <a name="see-also"></a>См. также
[Привязка элементов управления WPF к данным в Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
---
title: Привязка элементов управления к рисункам из базы данных | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
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
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: fbaca836cb5b620c596b72bc991e91c1cfc2312c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49189505"
---
# <a name="bind-controls-to-pictures-from-a-database"></a>Привязка элементов управления к рисункам из базы данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Можно использовать **источников данных** окно для привязки изображения в базе данных к элементу управления в приложении. Например, можно привязать к изображению <xref:System.Windows.Controls.Image> управления в приложении WPF или <xref:System.Windows.Forms.PictureBox> элемента управления в приложении Windows Forms.  
  
 Изображения в базе данных обычно хранятся в виде байтовых массивов. Элементы в **источников данных** окно, в котором хранятся в виде байтовых массивов имеют управления введите значение **None** по умолчанию, поскольку массивы байтов может содержать что угодно — от простого массива байтов до исполняемого файла большого приложения. Создание элемента управления с привязкой к данным для элемента массива байтов в **источников данных** окно, которое представляет изображение, необходимо выбрать элемент управления для создания.  
  
 Следующая процедура предполагает, что **источников данных** уже заполняется элементами, связанными с изображением. Дополнительные сведения см. в разделе [How to: Connect to Data in a Database](../data-tools/how-to-connect-to-data-in-a-database.md).  
  
### <a name="to-bind-a-picture-in-a-database-to-a-control"></a>Чтобы привязать изображение в базе данных к элементу управления  
  
1.  Убедитесь, что, в область конструктора, который вы хотите добавить элемент управления был открыт в конструкторе WPF или в конструкторе Windows Forms.  
  
2.  В **источников данных** окне разверните нужную таблицу или объект для отображения его свойств или столбцов.  
  
3.  Выберите столбец или свойство, которое содержит данные изображения и выберите один из следующих элементов управления из его управляющий элемент раскрывающегося списка:  
  
    -   Если открыт конструктор WPF, выберите **изображение**.  
  
    -   Если открыт конструктор Windows Forms, выберите **PictureBox**.  
  
    -   Кроме того можно выбрать другой элемент управления, который поддерживает привязку данных и может отображать изображения. Если элемент управления, который вы хотите использовать не в списке доступных элементов управления, можно добавить его в список и выберите ее. Дополнительные сведения см. в разделе [добавлять пользовательские элементы управления окна "Источники данных"](../data-tools/add-custom-controls-to-the-data-sources-window.md).  
  
## <a name="see-also"></a>См. также  
 [Привязка элементов управления WPF к данным в Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)


---
title: Пошаговое руководство. Прокрутка записей базы данных на листе
description: Узнайте, как с помощью конструктора можно отобразить одно поле из таблицы базы данных в листе Microsoft Excel.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Office development in Visual Studio], scrolling records
- records [Office development in Visual Studio], scrolling
- data [Office development in Visual Studio], scrolling database records
- worksheets [Office development in Visual Studio], scrolling records
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 29e6d4decf3d314654c4417f71bd7a2bad358b95
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949731"
---
# <a name="how-to-scroll-through-database-records-in-a-worksheet"></a>Пошаговое руководство. Прокрутка записей базы данных на листе
  В следующей процедуре показано, как использовать конструктор для отображения одного поля из таблицы базы данных в Microsoft Office листе Excel с элементами управления, которые позволяют конечному пользователю прокручивать все записи.

 Конструктор можно использовать только в проектах уровня документа. Однако можно также добавлять элементы управления и привязывать их к данным программным способом во время выполнения. Дополнительные сведения см. [в разделе Пошаговое руководство. Простая привязка данных в проекте надстройки VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="to-scroll-through-database-records-in-a-worksheet"></a>Прокрутка записей базы данных на листе

1. Откройте проект приложения Excel в Visual Studio.

2. Откройте окно **Источники данных** и создайте источник данных из базы данных. Дополнительные сведения см. в разделе [Добавление новых соединений](../data-tools/add-new-connections.md).

3. Разверните таблицу, содержащую данные, которые необходимо отобразить, и выберите конкретный столбец.

4. Откройте список элементов управления и выберите **NamedRange**.

5. Перетащите <xref:Microsoft.Office.Tools.Excel.NamedRange> элемент управления на ячейку, в которой должны отображаться данные.

6. На вкладке **Windows Forms** **панели элементов** добавьте <xref:System.Windows.Forms.BindingNavigator> элемент управления на лист и настройте элементы управления, которые хотите использовать. Дополнительные сведения см. в разделе [Общие сведения об элементе управления BindingNavigator &#40;Windows Forms&#41;](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).

## <a name="see-also"></a>См. также раздел
- [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)

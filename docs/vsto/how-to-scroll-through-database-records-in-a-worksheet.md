---
title: Практическое руководство. Прокрутка записей базы данных на листе
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f0b3c6a8a9292ceda03c9d0020b78d9518ca49d9
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/25/2019
ms.locfileid: "71252035"
---
# <a name="how-to-scroll-through-database-records-in-a-worksheet"></a>Практическое руководство. Прокрутка записей базы данных на листе
  В следующей процедуре показано, как использовать конструктор для отображения одного поля из таблицы базы данных в Microsoft Office листе Excel с элементами управления, которые позволяют конечному пользователю прокручивать все записи.

 Конструктор можно использовать только в проектах уровня документа. Однако можно также добавлять элементы управления и привязывать их к данным программным способом во время выполнения. Дополнительные сведения см. в разделе [Пошаговое руководство: Простая привязка данных в проекте](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)надстройки VSTO.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

## <a name="to-scroll-through-database-records-in-a-worksheet"></a>Прокрутка записей базы данных на листе

1. Откройте проект приложения Excel в Visual Studio.

2. Откройте окно **Источники данных** и создайте источник данных из базы данных. Дополнительные сведения см. в разделе [Добавление новых соединений](../data-tools/add-new-connections.md).

3. Разверните таблицу, содержащую данные, которые необходимо отобразить, и выберите конкретный столбец.

4. Откройте список элементов управления и выберите **NamedRange**.

5. <xref:Microsoft.Office.Tools.Excel.NamedRange> Перетащите элемент управления на ячейку, в которой должны отображаться данные.

6. На вкладке **Windows Forms** **панели элементов**добавьте <xref:System.Windows.Forms.BindingNavigator> элемент управления на лист и настройте элементы управления, которые хотите использовать. Дополнительные сведения см. в разделе [Общие сведения &#40;об&#41;элементе управления BindingNavigator Windows Forms](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).

## <a name="see-also"></a>См. также
- [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)

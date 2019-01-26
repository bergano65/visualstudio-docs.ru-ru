---
title: Как выполнить Прокрутить записи базы данных на листе
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
ms.openlocfilehash: 47a95db3797592f4c8d55ffa72e0e7323d251378
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/24/2019
ms.locfileid: "54863608"
---
# <a name="how-to-scroll-through-database-records-in-a-worksheet"></a>Как выполнить Прокрутить записи базы данных на листе
  Ниже показано, как использовать конструктор для отображения одно поле из таблицы базы данных в лист Microsoft Office Excel, с помощью элементов управления, которые позволяют пользователю просматривать все записи.  
  
 Конструктор можно использовать только в проектах уровня документа. Тем не менее можно также добавлять элементы управления и привязать их к данным программными средствами во время выполнения. Дополнительные сведения см. в разделе [Пошаговое руководство: Простая привязка данных в проекте надстройки VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
## <a name="to-scroll-through-database-records-in-a-worksheet"></a>Чтобы прокрутить записи базы данных на листе  
  
1.  Откройте проект приложения Excel в Visual Studio.  
  
2.  Откройте **источников данных** окно и создать источник данных из базы данных. Дополнительные сведения см. в разделе [Добавление новых подключений](../data-tools/add-new-connections.md).  
  
3.  Разверните таблицу, которая содержит данные, которые требуется отобразить и выберите нужный столбец.  
  
4.  Откройте список элементов управления и выберите **NamedRange**.  
  
5.  Перетащите <xref:Microsoft.Office.Tools.Excel.NamedRange> элемента управления на ячейку, где должны отображаться данные.  
  
6.  Из **Windows Forms** вкладке **элементов**, добавьте <xref:System.Windows.Forms.BindingNavigator> управления на лист и настроить элементы управления, которые вы хотите использовать. Дополнительные сведения см. в разделе [Обзор элемента управления BindingNavigator &#40;Windows Forms&#41;](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).  
  
## <a name="see-also"></a>См. также  
 [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)  

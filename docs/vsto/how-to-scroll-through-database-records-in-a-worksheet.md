---
title: 'Практическое: прокрутка записей базы данных на листе'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- databases [Office development in Visual Studio], scrolling records
- records [Office development in Visual Studio], scrolling
- data [Office development in Visual Studio], scrolling database records
- worksheets [Office development in Visual Studio], scrolling records
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7e9ffaffdefda98e3e074467fcd4df8cacce91b4
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/06/2018
ms.locfileid: "35674874"
---
# <a name="how-to-scroll-through-database-records-in-a-worksheet"></a>Практическое: прокрутка записей базы данных на листе
  Ниже показано, как использовать конструктор для отображения одно поле из таблицы базы данных в лист Microsoft Office Excel, с помощью элементов управления, которые позволяют пользователю просматривать все записи.  
  
 Конструктор можно использовать только в проектах уровня документа. Тем не менее можно также добавлять элементы управления и привязать их к данным программными средствами во время выполнения. Дополнительные сведения см. в разделе [Пошаговое руководство: простая привязка данных в проекте надстройки VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).  
  
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
  
  
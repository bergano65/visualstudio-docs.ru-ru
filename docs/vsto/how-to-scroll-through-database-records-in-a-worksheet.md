---
title: "Как: прокрутка записей базы данных на листе | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
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
manager: ghogen
ms.workload: office
ms.openlocfilehash: f7e6ea8269401a8b026da2562eff96e50820e0a0
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="how-to-scroll-through-database-records-in-a-worksheet"></a>Практическое руководство. Прокрутка записей базы данных на листе
  Ниже показано, как использовать конструктор для отображения одного поля из таблицы базы данных в лист Microsoft Office Excel, с помощью элементов управления, позволяющие конечным пользователям прокручивать все записи.  
  
 Конструктор можно использовать только в проектах уровня документа. Тем не менее можно добавить элементы управления и привязать их к данным программными средствами во время выполнения. Дополнительные сведения см. в разделе [Пошаговое руководство: простая привязка данных в VSTO надстройки проекта](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
### <a name="to-scroll-through-database-records-in-a-worksheet"></a>Прокрутка записей базы данных на листе  
  
1.  Откройте проект приложения Excel в Visual Studio.  
  
2.  Откройте **источники данных** окно и создать источник данных из базы данных. Дополнительные сведения см. в разделе [Добавление новых подключений](../data-tools/add-new-connections.md).  
  
3.  Разверните таблицу, которая содержит данные, которые требуется отобразить и выберите нужный столбец.  
  
4.  Откройте список элементов управления и выберите **NamedRange**.  
  
5.  Перетащите <xref:Microsoft.Office.Tools.Excel.NamedRange> управления на ячейку, в котором должны отображаться данные.  
  
6.  Из **Windows Forms** вкладке **элементов**, добавьте <xref:System.Windows.Forms.BindingNavigator> управления на лист и настроить элементы управления, которые вы хотите использовать. Дополнительные сведения см. в разделе [Обзор элемента управления BindingNavigator &#40; Windows Forms &#41; ](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).  
  
## <a name="see-also"></a>См. также  
 [Привязка данных к элементам управления в решениях Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  
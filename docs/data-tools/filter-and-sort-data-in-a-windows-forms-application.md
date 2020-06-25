---
title: Фильтрация и сортировка данных в приложении Windows Forms
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- row states, filtering
- data views, sorting
- row version, filtering
- row states
- data views, filtering
- sorting datasets, using data views
- dataset filtering, using data views
ms.assetid: f4f100f1-776d-46dc-b2fd-5b35b98d9561
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7c420896a883146cf60de414100fc41080220e36
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/23/2020
ms.locfileid: "85282388"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Фильтрация и сортировка данных в приложении Windows Forms

Данные фильтруются путем присвоения <xref:System.Windows.Forms.BindingSource.Filter%2A> свойству строкового выражения, возвращающего нужные записи.

Данные сортируются путем присвоения <xref:System.Windows.Forms.BindingSource.Sort%2A> свойству имени столбца, по которому нужно выполнить сортировку; добавление `DESC` в сортировку в убывающем порядке или добавление `ASC` к сортировке по возрастанию.

> [!NOTE]
> Если приложение не использует <xref:System.Windows.Forms.BindingSource> компоненты, можно фильтровать и сортировать данные с помощью <xref:System.Data.DataView> объектов. Дополнительные сведения см. в разделе " [представления](/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews)данных".

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>Фильтрация данных с помощью компонента BindingSource

- Задайте <xref:System.Windows.Forms.BindingSource.Filter%2A> для свойства выражение, которое требуется вернуть. Например, следующий код возвращает клиентов с `CompanyName` , который начинается с "B":

     [!code-csharp[VbRaddataDisplaying#6](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_1.cs)]
     [!code-vb[VbRaddataDisplaying#6](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_1.vb)]

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>Сортировка данных с помощью компонента BindingSource

- Задайте <xref:System.Windows.Forms.BindingSource.Sort%2A> для свойства столбец, по которому необходимо выполнить сортировку. Например, следующий код сортирует клиентов по `CompanyName` столбцу в убывающем порядке:

     [!code-csharp[VbRaddataDisplaying#7](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_2.cs)]
     [!code-vb[VbRaddataDisplaying#7](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_2.vb)]

## <a name="see-also"></a>См. также

- [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)

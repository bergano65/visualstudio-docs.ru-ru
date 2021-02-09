---
title: Фильтрация и сортировка данных в приложении Windows Forms
description: Фильтрация и сортировка данных в приложении Windows Forms. Задайте для свойства фильтра строковое выражение, возвращающее нужные записи.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: b1708d6871f1acdf437895563d9b5a39dbe93f21
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858856"
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

## <a name="see-also"></a>См. также раздел

- [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)

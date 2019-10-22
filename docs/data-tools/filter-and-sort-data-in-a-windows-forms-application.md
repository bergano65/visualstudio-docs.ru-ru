---
title: Фильтрация и сортировка данных в приложении Windows Forms
ms.date: 11/04/2016
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 68adaf6df9f97bee94e7cb393fa01ee133444c80
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648459"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Фильтрация и сортировка данных в приложении Windows Forms

Данные фильтруются путем присвоения свойству <xref:System.Windows.Forms.BindingSource.Filter%2A> строкового выражения, возвращающего нужные записи.

Данные сортируются путем присвоения свойству <xref:System.Windows.Forms.BindingSource.Sort%2A> имени столбца, по которому нужно выполнить сортировку; Добавьте `DESC` для сортировки в убывающем порядке или добавьте `ASC` для сортировки в возрастающем порядке.

> [!NOTE]
> Если приложение не использует <xref:System.Windows.Forms.BindingSource> компоненты, можно фильтровать и сортировать данные с помощью <xref:System.Data.DataView> объектов. Дополнительные сведения см. в разделе " [представления](/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews)данных".

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>Фильтрация данных с помощью компонента BindingSource

- Задайте для свойства <xref:System.Windows.Forms.BindingSource.Filter%2A> выражение, которое требуется вернуть. Например, следующий код возвращает клиентов с `CompanyName`, начинающейся с "B":

     [!code-csharp[VbRaddataDisplaying#6](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_1.cs)]
     [!code-vb[VbRaddataDisplaying#6](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_1.vb)]

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>Сортировка данных с помощью компонента BindingSource

- Задайте для свойства <xref:System.Windows.Forms.BindingSource.Sort%2A> столбец, по которому необходимо выполнить сортировку. Например, следующий код сортирует клиентов по столбцу `CompanyName` в убывающем порядке:

     [!code-csharp[VbRaddataDisplaying#7](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_2.cs)]
     [!code-vb[VbRaddataDisplaying#7](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_2.vb)]

## <a name="see-also"></a>См. также

- [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
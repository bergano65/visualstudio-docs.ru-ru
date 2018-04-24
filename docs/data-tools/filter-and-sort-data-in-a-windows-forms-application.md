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
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: ff5c31b14f13252fbcad0f42762627a14e610591
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Фильтрация и сортировка данных в приложении Windows Forms
Фильтрация данных, задав <xref:System.Windows.Forms.BindingSource.Filter%2A> свойства строковое выражение, возвращающее нужные записи.

 Сортировка данных, задав <xref:System.Windows.Forms.BindingSource.Sort%2A> свойство для имени столбца, сортировки, добавлять `DESC` отсортировать в нисходящем порядке или добавить `ASC` для сортировки по возрастанию.

> [!NOTE]
>  Если приложение использует <xref:System.Windows.Forms.BindingSource> компонентов, можно фильтровать и сортировать данные с помощью <xref:System.Data.DataView> объектов. Дополнительные сведения см. в разделе [объекты DataView](/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews).

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>Для фильтрации данных с помощью компонента BindingSource

-   Задать <xref:System.Windows.Forms.BindingSource.Filter%2A> свойства выражения, необходимо вернуть. Например, следующий код возвращает клиентов с `CompanyName` , начинающегося с «B»:

     [!code-csharp[VbRaddataDisplaying#6](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_1.cs)]
     [!code-vb[VbRaddataDisplaying#6](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_1.vb)]

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>Сортировка данных с помощью компонента BindingSource

-   Задать <xref:System.Windows.Forms.BindingSource.Sort%2A> свойства столбца, необходимо выполнить сортировку. Например, следующий код сортирует клиентов по `CompanyName` столбца в убывающем порядке:

     [!code-csharp[VbRaddataDisplaying#7](../data-tools/codesnippet/CSharp/filter-and-sort-data-in-a-windows-forms-application_2.cs)]
     [!code-vb[VbRaddataDisplaying#7](../data-tools/codesnippet/VisualBasic/filter-and-sort-data-in-a-windows-forms-application_2.vb)]

## <a name="see-also"></a>См. также

- [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
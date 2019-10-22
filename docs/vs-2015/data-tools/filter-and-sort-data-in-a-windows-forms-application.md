---
title: Фильтрация и сортировка данных в приложении Windows Forms | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- row states, filtering
- data views, sorting
- row version, filtering
- row states
- data views, filtering
- sorting datasets, using data views
- dataset filtering, using data views
ms.assetid: f4f100f1-776d-46dc-b2fd-5b35b98d9561
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 24c623efc141ff84c2585f967596271d1efbc502
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671650"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Фильтрация и сортировка данных в приложении Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Данные фильтруются путем присвоения свойству <xref:System.Windows.Forms.BindingSource.Filter%2A> строкового выражения, возвращающего нужные записи.

 Данные сортируются путем присвоения свойству <xref:System.Windows.Forms.BindingSource.Sort%2A> имени столбца, по которому нужно выполнить сортировку; Добавьте `DESC` для сортировки в убывающем порядке или добавьте `ASC` для сортировки в возрастающем порядке.

> [!NOTE]
> Если приложение не использует <xref:System.Windows.Forms.BindingSource> компоненты, можно фильтровать и сортировать данные с помощью <xref:System.Data.DataView> объектов. Дополнительные сведения см. в разделе " [представления](https://msdn.microsoft.com/library/0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b)данных".

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>Фильтрация данных с помощью компонента BindingSource

- Задайте для свойства <xref:System.Windows.Forms.BindingSource.Filter%2A> выражение, которое требуется вернуть. Например, следующий код возвращает клиентов с `CompanyName`, начинающейся с "B":

     [!code-csharp[VbRaddataDisplaying#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#6)]
     [!code-vb[VbRaddataDisplaying#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#6)]

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>Сортировка данных с помощью компонента BindingSource

- Задайте для свойства <xref:System.Windows.Forms.BindingSource.Sort%2A> столбец, по которому необходимо выполнить сортировку. Например, следующий код сортирует клиентов по столбцу `CompanyName` в убывающем порядке:

     [!code-csharp[VbRaddataDisplaying#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#7)]
     [!code-vb[VbRaddataDisplaying#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#7)]

## <a name="see-also"></a>См. также раздел
 [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)

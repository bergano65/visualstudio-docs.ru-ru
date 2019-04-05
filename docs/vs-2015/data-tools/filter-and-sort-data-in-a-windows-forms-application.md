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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5592a488788c61af7ad6875de239fca62746857c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58979000"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Фильтрация и сортировка данных в приложении Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Фильтрация данных, задав <xref:System.Windows.Forms.BindingSource.Filter%2A> свойства строковое выражение, возвращающее нужные записи.  
  
 Сортировать данные, задав <xref:System.Windows.Forms.BindingSource.Sort%2A> свойства имя столбца, сортировка по; добавьте `DESC` отсортировать в нисходящем порядке или добавить `ASC` для сортировки по возрастанию.  
  
> [!NOTE]
>  Если приложение не использует <xref:System.Windows.Forms.BindingSource> компонентов, можно фильтровать и сортировать данные с помощью <xref:System.Data.DataView> объектов. Дополнительные сведения см. в разделе [объекты DataView](http://msdn.microsoft.com/library/0fe5dfa2-c1cd-435f-90b6-b4dd2e3ef34b).  
  
## <a name="to-filter-data-by-using-a-bindingsource-component"></a>Для фильтрации данных с помощью компонента BindingSource  
  
-   Задайте <xref:System.Windows.Forms.BindingSource.Filter%2A> значение выражения, который необходимо вернуть. Например, следующий код возвращает клиентов с `CompanyName` , начинающегося с «B»:  
  
     [!code-csharp[VbRaddataDisplaying#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#6)]
     [!code-vb[VbRaddataDisplaying#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#6)]  
  
## <a name="to-sort-data-by-using-a-bindingsource-component"></a>Для сортировки данных с помощью компонента BindingSource  
  
-   Задать <xref:System.Windows.Forms.BindingSource.Sort%2A> свойства столбца, нужно выполнить сортировку. Например, следующий код сортирует клиентов по `CompanyName` столбец в порядке убывания:  
  
     [!code-csharp[VbRaddataDisplaying#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs#7)]
     [!code-vb[VbRaddataDisplaying#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb#7)]  
  
## <a name="see-also"></a>См. также  
 [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)

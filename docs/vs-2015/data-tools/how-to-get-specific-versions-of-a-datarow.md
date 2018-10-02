---
title: 'Практическое: получение определенных версий объекта DataRow | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- row states
- updating datasets, row states
- DataRow object
ms.assetid: d7cde25e-cef5-4559-b994-be00e258ac1f
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: ed409bdafaa15052a7190480a7cbc46ac766de84
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559563"
---
# <a name="how-to-get-specific-versions-of-a-datarow"></a>Практическое руководство. Получение определенных версий объекта DataRow
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

При внесении изменений в строки данных, набора данных сохраняет исходные (<xref:System.Data.DataRowVersion>) и new (<xref:System.Data.DataRowVersion>) версии строки. Например, перед вызовом `AcceptChanges` метод, приложение может получить доступ в разных версиях запись (как определено в <xref:System.Data.DataRowVersion> перечисления) и соответственно обрабатывать изменения.  
  
> [!NOTE]
>  Существуют различные версии строки, только после его изменения и перед ему были `AcceptChanges` метод с именем. После `AcceptChanges` был вызван метод, текущие и исходные версии ничем не отличаются.  
  
 Передача <xref:System.Data.DataRowVersion> значение вместе с индексом столбца (или имя столбца в виде строки) возвращает значение из версии конкретной строки этого столбца. Измененный столбец определяется во время <xref:System.Data.DataTable.ColumnChanging> и <xref:System.Data.DataTable.ColumnChanged> события, это хорошая возможность проверить отличающийся строки версии в целях проверки. Однако если ограничения временно приостановлена, эти события не возникнет, и вам потребуется могут программно определять, какие столбцы были изменены. Это можно сделать с помощью итерации <xref:System.Data.DataTable.Columns%2A> сбора и сравнения различных <xref:System.Data.DataRowVersion> значения.  
  
## <a name="accessing-the-original-version-of-a-datarow"></a>Доступ к исходной версии DataRow  
  
#### <a name="to-get-the-original-version-of-a-record"></a>Чтобы просмотреть его исходную версию записи  
  
-   Доступ к значению столбца, передав <xref:System.Data.DataRowVersion> строки, который необходимо вернуть.  
  
     В следующем примере показано, как можно использовать <xref:System.Data.DataRowVersion> значение, чтобы получить исходное значение `CompanyName` в <xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#21](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#21)]
     [!code-vb[VbRaddataEditing#21](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#21)]  
  
## <a name="accessing-the-current-version-of-a-datarow"></a>Доступ к текущей версии DataRow  
  
#### <a name="to-get-the-current-version-of-a-record"></a>Для получения текущей версии записи  
  
-   Доступ к значению столбца и добавьте параметр в индекс, указывающий, какая версия строки необходимо вернуть.  
  
     В следующем примере показано, как можно использовать <xref:System.Data.DataRowVersion> значение, чтобы получить текущее значение `CompanyName` в <xref:System.Data.DataRow>:  
  
     [!code-csharp[VbRaddataEditing#22](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataEditing/CS/Form1.cs#22)]
     [!code-vb[VbRaddataEditing#22](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataEditing/VB/Form1.vb#22)]  
  
## <a name="see-also"></a>См. также  
 [Редактирование данных в приложении](../data-tools/editing-data-in-your-application.md)   
 [Проверка данных](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Сохранение данных](../data-tools/saving-data.md)   
 [Примеры работы с данными](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Привязка элементов управления Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Общие сведения о данных приложений в Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Подключение к данным в Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Подготовка приложения для получения данных](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Выборка данных в приложение](../data-tools/fetching-data-into-your-application.md)   
 [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
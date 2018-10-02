---
title: 'Практическое: заполнения набора данных с данными | Документация Майкрософт'
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
- TableAdapter.GetData
- TableAdapter.Fill
- datasets [Visual Basic], filling
- DataTable objects, loading
- data [Visual Basic], loading into datasets
ms.assetid: 7ab436d4-54ba-4621-902f-3f193279e18c
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: c2bba5c7bcdf1453129c6c3677e750c0e5599bac
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568243"
---
# <a name="how-to-fill-a-dataset-with-data"></a>Практическое: заполнения набора данных с данными
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Фраза «заполнение набора данных» относится к загрузке данных в отдельные <xref:System.Data.DataTable> объекты, составляющие набор данных. Таблицы данных заполняются путем выполнения запросов адаптера таблицы или путем выполнения адаптера данных (например, <xref:System.Data.SqlClient.SqlDataAdapter>) команд.  
  
 Следует ли использовать адаптеры таблиц или адаптеров данных зависит от того, как был создан набор данных. Если вы использовали средства проектирования в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], такие как [мастер настройки источника данных](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f), набор данных содержит адаптеры таблицы. Дополнительные сведения о адаптеры таблиц, см. в разделе [TableAdapter Overview](../data-tools/tableadapter-overview.md). При создании набора данных программными средствами, обычно необходимо будет создать адаптеры данных для загрузки данных в таблицах данных.  
  
> [!NOTE]
>  При перетаскивании элементов из [окна "Источники данных"](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) на форму код для заполнения таблицы данными автоматически добавляется `Form_Load` обработчик событий. Откройте форму в редакторе кода для просмотра точного синтаксиса для заполнения отдельных таблиц. Если вы не хотите заполнения таблицы при загрузке формы, можно переместить этот код в другой метод, или удалите его вообще.  
  
## <a name="filling-a-dataset-using-a-tableadapter"></a>Заполнение набора данных с помощью адаптера таблицы  
 Запрос можно вызвать в TableAdapter для загрузки данных в таблицы данных в наборе данных. Передайте <xref:System.Data.DataTable> необходимо заполнить для запроса адаптера таблицы. Если запрос использует параметры, передайте их в метод, а также. Если набор данных содержит несколько таблиц, вы должны иметь отдельные адаптеры таблиц для каждой таблицы и поэтому должен заполнять каждую таблицу отдельно.  
  
> [!NOTE]
>  По умолчанию каждый раз при выполнении запроса адаптера таблицы, данные в таблице очищаются до результаты запроса, загружаемых в таблицу. Можно сохранить существующие данные в таблице и добавление результатов, задав TableAdapter `ClearBeforeFill` свойства `false`.  
  
#### <a name="to-fill-a-dataset-with-data-using-a-tableadapter"></a>Для заполнения набора данных с помощью адаптера таблицы  
  
1.  Откройте форму или компонент в **редактор кода**.  
  
2.  Добавьте код в любом месте в приложении, где необходимо загрузить данные в таблицу с данными. Если запрос не принимает параметров, передайте <xref:System.Data.DataTable> необходимо заполнить. Код должен выглядеть следующим образом:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#4)]
     [!code-vb[VbRaddataFillingAndExecuting#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#4)]  
  
3.  Если запрос использует параметры, передайте <xref:System.Data.DataTable> нужно заполнить и параметры, ожидаемые запросом. В зависимости от фактических параметров в запросе код будет выглядеть аналогично приведенным ниже:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#5)]
     [!code-vb[VbRaddataFillingAndExecuting#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#5)]  
  
## <a name="filling-a-dataset-using-a-dataadapter"></a>Заполнение набора данных с помощью DataAdapter  
 Вызовите адаптера данных `Fill` метод. В результате адаптер для выполнения инструкции SQL или хранимой процедуры, ссылающихся на них его `SelectCommand` свойство и помещать результаты в таблицу в наборе данных. Если набор данных содержит несколько таблиц, вы должны иметь отдельный адаптер данных для каждой таблицы и поэтому должен заполнять каждую таблицу отдельно.  
  
#### <a name="to-fill-a-dataset-with-data-using-a-dataadapter"></a>Для заполнения набора данных с помощью адаптера данных DataAdapter  
  
-   Вызовите <xref:System.Data.Common.DataAdapter.Fill%2A> метод <xref:System.Data.Common.DataAdapter>, передавая <xref:System.Data.DataSet> или <xref:System.Data.DataTable> для загрузки данных. Пример:  
  
     [!code-csharp[VbRaddataFillingAndExecuting#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form2.cs#6)]
     [!code-vb[VbRaddataFillingAndExecuting#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form2.vb#6)]  
  
     Как правило, необходимо предоставить имя <xref:System.Data.DataTable> для загрузки данных. Если передать имя <xref:System.Data.DataSet> вместо конкретной таблицы данных, <xref:System.Data.DataTable> с именем `Table1` добавляется в набор данных и загружена с результатами из базы данных (в отличие от загрузки данных в существующем <xref:System.Data.DataTable> в наборе данных). Дополнительные сведения см. в разделе [заполнение набора данных из объекта DataAdapter](http://msdn.microsoft.com/library/3fa0ac7d-e266-4954-bfac-3fbe2f913153).  
  
## <a name="see-also"></a>См. также  
 [Заполнение наборов данных с помощью адаптера таблицы](../data-tools/fill-datasets-by-using-tableadapters.md)   
 [Выборка данных в приложение](../data-tools/fetching-data-into-your-application.md)   
 [Подготовка приложения для получения данных](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Редактирование данных в приложении](../data-tools/editing-data-in-your-application.md)   
 [Проверка данных](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Сохранение данных](../data-tools/saving-data.md)
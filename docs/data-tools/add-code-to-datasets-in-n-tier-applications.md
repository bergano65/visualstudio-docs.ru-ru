---
title: "Практическое руководство. Добавление кода для наборов данных в многоуровневых приложениях | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "многоуровные приложения, расширение наборов данных"
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
caps.latest.revision: 20
caps.handback.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Практическое руководство. Добавление кода для наборов данных в многоуровневых приложениях
Можно расширить функциональные возможности набора данных путем создания файла разделяемого класса и добавления к нему кода \(вместо добавления кода к файлу *DatasetName*. DataSet.Designer\).  \(Разделяемые классы позволяют разделять код для определенного класса между несколькими физическими файлами.  Дополнительные сведения см. в разделе [Partial](/dotnet/visual-basic/language-reference/modifiers/partial) или [Разделяемые классы и методы](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).\)  
  
 Код, определяющий набор данных, создается при каждом внесении изменений в определение набора данных \(в [Создание и изменение типизированных наборов данных](../data-tools/creating-and-editing-typed-datasets.md)\).  Этот код также создается при внесении изменений во время выполнения мастеров, изменяющих конфигурацию набора данных.  Чтобы предотвратить удаление кода во время повторного формирования набора данных, добавьте код в файл разделяемого класса набора данных.  
  
 По умолчанию результатом разделения кода набора данных и кода `TableAdapter` являются отдельные файлы классов в каждом проекте.  Исходный проект включает файл с именем *DatasetName*.Designer.vb \(или *DatasetName*.Designer.cs\), содержащий код `TableAdapter`.  Проект, указанный в свойстве **Проект набора данных**, включает файл с именем *DatasetName*.DataSet.Designer.vb \(или *DatasetName*.DataSet.Designer.cs\), содержащий код набора данных.  
  
> [!NOTE]
>  После разделения наборов данных и `TableAdapter` \(путем установки свойства **Проект набора данных**\) существующие в проекте разделяемые классы наборов данных не будут перемещаться автоматически.  Существующие разделяемые классы наборов данных должны быть вручную перемещены в проект набора данных.  
  
> [!NOTE]
>  [Создание и изменение типизированных наборов данных](../data-tools/creating-and-editing-typed-datasets.md) также предоставляет функциональные возможности для создания обработчиков событий <xref:System.Data.DataTable.ColumnChanging> и <xref:System.Data.DataTable.RowChanging> при добавлении кода проверки.  Дополнительные сведения см. в разделе [Практическое руководство. Добавление проверки в N\-уровневом наборе данных](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
### Добавление кода для наборов данных в многоуровневых приложениях  
  
1.  Найдите проект, который содержит XSD\-файл \([Создание и изменение типизированных наборов данных](../data-tools/creating-and-editing-typed-datasets.md)\).  
  
2.  Дважды щелкните файл **.xsd**, чтобы открыть [Создание и изменение типизированных наборов данных](../data-tools/creating-and-editing-typed-datasets.md).  
  
3.  Щелкните правой кнопкой мыши таблицу данных, для которой требуется добавить код \(имя таблицы в области заголовка\), и нажмите кнопку **Просмотреть код**.  
  
     Созданный разделяемый класс открывается в редакторе кода.  
  
4.  Добавьте код внутри объявления разделяемого класса.  
  
     В следующем примере показано место для добавления кода в CustomersDataTable в NorthwindDataSet:  
  
    ```vb#  
    Partial Public Class CustomersDataTable  
        ' Add code here to add functionality   
        ' to the CustomersDataTable.  
    End Class  
    ```  
  
    ```c#  
    partial class CustomersDataTable  
    {  
        // Add code here to add functionality  
        // to the CustomersDataTable.  
    }  
    ```  
  
## См. также  
 [Общие сведения о N\-уровневых приложениях для работы с данными](../data-tools/n-tier-data-applications-overview.md)   
 [Практическое руководство. Добавление кода для объектов TableAdapter в многоуровневых приложениях](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)   
 [адаптеры таблиц TableAdapter](../Topic/TableAdapters.md)   
 [Общие сведения о компоненте TableAdapterManager](../Topic/TableAdapterManager%20Overview.md)   
 [Общие сведения об иерархическом обновлении](../Topic/Hierarchical%20Update%20Overview.md)   
 [Создание приложений для работы с данными](../data-tools/creating-data-applications.md)   
 [Работа с наборами данных в Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
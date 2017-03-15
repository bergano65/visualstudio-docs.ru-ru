---
title: "Практическое руководство. Добавление кода для объектов TableAdapter в многоуровневых приложениях | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "многоуровные приложения, расширение TableAdapters"
  - "адаптеры таблиц TableAdapter, многоуровные приложения"
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
caps.latest.revision: 19
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Практическое руководство. Добавление кода для объектов TableAdapter в многоуровневых приложениях
Можно расширить функциональные возможности `TableAdapter` путем создания файла разделяемого класса для `TableAdapter` и добавления к нему кода \(вместо добавления кода к файлу *DatasetName*. DataSet.Designer\).  \(Разделяемые классы позволяют разделять код для определенного класса между несколькими физическими файлами.  Дополнительные сведения см. в разделе [Partial](/dotnet/visual-basic/language-reference/modifiers/partial) или [partial \(тип\)](/dotnet/csharp/language-reference/keywords/partial-type).\)  
  
 Код, определяющий `TableAdapter`, создается при каждом внесении изменений в `TableAdapter` \(в [Создание и изменение типизированных наборов данных](../data-tools/creating-and-editing-typed-datasets.md)\).  Этот код также создается при внесении изменений во время выполнения мастеров, изменяющих конфигурацию `TableAdapter`.  Чтобы предотвратить удаление кода во время повторного формирования `TableAdapter`, добавьте код в файл разделяемого класса `TableAdapter`.  
  
 По умолчанию результатом разделения кода набора данных и кода `TableAdapter` являются отдельные файлы классов в каждом проекте.  Исходный проект включает файл с именем *DatasetName*.Designer.vb \(или *DatasetName*.Designer.cs\), содержащий код `TableAdapter`.  Проект, указанный в свойстве **Проект набора данных**, включает файл с именем *DatasetName*.DataSet.Designer.vb \(или *DatasetName*.DataSet.Designer.cs\), содержащий код набора данных.  
  
> [!NOTE]
>  После разделения наборов данных и `TableAdapter` \(путем установки свойства **Проект набора данных**\) существующие в проекте разделяемые классы наборов данных не будут перемещаться автоматически.  Существующие разделяемые классы наборов данных должны быть вручную перемещены в проект набора данных.  
  
> [!NOTE]
>  [Создание и изменение типизированных наборов данных](../data-tools/creating-and-editing-typed-datasets.md) также предоставляет функциональные возможности для создания обработчиков событий <xref:System.Data.DataTable.ColumnChanging> и <xref:System.Data.DataTable.RowChanging> при добавлении кода проверки.  Дополнительные сведения см. в разделе [Практическое руководство. Добавление проверки в N\-уровневом наборе данных](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### Чтобы добавить пользовательский код к TableAdapter в многоуровневом приложении:  
  
1.  Найдите проект, который содержит XSD\-файл \([Создание и изменение типизированных наборов данных](../data-tools/creating-and-editing-typed-datasets.md)\).  
  
2.  Дважды щелкните файл **.xsd**, чтобы открыть [Создание и изменение типизированных наборов данных](../data-tools/creating-and-editing-typed-datasets.md).  
  
3.  Щелкните правой кнопкой мыши `TableAdapter`, в который требуется добавить код, и нажмите кнопку **Просмотреть код**.  
  
     Созданный разделяемый класс открывается в редакторе кода.  
  
4.  Добавьте код внутри объявления разделяемого класса.  
  
5.  В следующем примере показано место для добавления кода в `CustomersTableAdapter` в `NorthwindDataSet`:  
  
    ```vb#  
    Partial Public Class CustomersTableAdapter  
        ' Add code here to add functionality   
        ' to the CustomersTableAdapter.  
    End Class  
    ```  
  
    ```c#  
    public partial class CustomersTableAdapter  
    {  
        // Add code here to add functionality  
        // to the CustomersTableAdapter.  
    }  
    ```  
  
## См. также  
 [Общие сведения о N\-уровневых приложениях для работы с данными](../data-tools/n-tier-data-applications-overview.md)   
 [Практическое руководство. Добавление кода для наборов данных в многоуровневых приложениях](../data-tools/add-code-to-datasets-in-n-tier-applications.md)   
 [адаптеры таблиц TableAdapter](../Topic/TableAdapters.md)   
 [Общие сведения о компоненте TableAdapterManager](../Topic/TableAdapterManager%20Overview.md)   
 [Общие сведения об иерархическом обновлении](../Topic/Hierarchical%20Update%20Overview.md)   
 [Создание приложений для работы с данными](../data-tools/creating-data-applications.md)
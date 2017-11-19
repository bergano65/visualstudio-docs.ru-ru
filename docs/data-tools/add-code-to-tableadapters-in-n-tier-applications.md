---
title: "Добавьте код для объектов TableAdapter в многоуровневых приложениях | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 396e1132015c2eb37f06095f135dae878bfeb574
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>Добавьте код для объектов TableAdapter в многоуровневых приложениях
Можно расширить функциональные возможности адаптера таблицы путем создания файла разделяемого класса для адаптера таблицы и добавления к нему кода (вместо добавления кода в *DatasetName*. DataSet.Designer-файл). Разделяемые классы позволяют коду для определенного класса разделяться между несколькими физическими файлами. Дополнительные сведения см. в разделе [частичного](/dotnet/visual-basic/language-reference/modifiers/partial) или [partial (тип)](/dotnet/csharp/language-reference/keywords/partial-type).  
  
Код, определяющий адаптер таблицы создается каждый раз при внесении изменений в адаптер таблицы в наборе данных. Этот код также создается при внесении изменений во время выполнения мастеров, изменяющих конфигурацию адаптера таблицы. Чтобы предотвратить удаление во время повторного формирования адаптера таблицы в коде, добавьте код в файл разделяемого класса адаптера таблицы.  
  
По умолчанию после разделения кода адаптера таблицы и набора данных получается отдельные файлы классов в каждом проекте. Исходный проект содержит файл с именем *DatasetName*. Designer.vb (или *DatasetName*. Designer.cs), содержащий код адаптера таблицы. Проект, который назначен в **Dataset проекта** свойство имеет файл с именем *DatasetName*. DataSet.Designer.vb (или *DatasetName*. DataSet.Designer.cs), содержащий код набора данных.  
  
> [!NOTE]
>  При разделении наборов данных и адаптеров таблиц (установив **DataSet проекта** свойства), существующие разделяемые классы наборов данных в проекте не перемещаются автоматически. Существующие разделяемые классы наборов данных должны быть вручную перемещены в проект набора данных.  
  
> [!NOTE]
>  Набор данных предоставляет функциональные возможности для создания <xref:System.Data.DataTable.ColumnChanging> и <xref:System.Data.DataTable.RowChanging> обработчики событий, когда требуется проверка. Дополнительные сведения см. в разделе [Добавление проверки в n уровневом наборе данных](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>Добавление пользовательского кода в TableAdapter в многоуровневых приложениях  
  
1.  Найдите проект, который содержит файл с расширением XSD.
  
2.  Дважды щелкните **.xsd** файл, чтобы открыть **конструктора наборов данных**.  
  
3.  Щелкните правой кнопкой мыши TableAdapter, который требуется добавить код, а затем выберите **Просмотр кода**.  
  
     Разделяемый класс создается и открывается в редакторе кода.  
  
4.  Добавьте код в объявление разделяемого класса.  
  
5.  В следующем примере показано, куда нужно добавить код для `CustomersTableAdapter` в `NorthwindDataSet`:  
  
    ```vb  
    Partial Public Class CustomersTableAdapter  
        ' Add code here to add functionality   
        ' to the CustomersTableAdapter.  
    End Class  
    ```  
  
    ```csharp  
    public partial class CustomersTableAdapter  
    {  
        // Add code here to add functionality  
        // to the CustomersTableAdapter.  
    }  
    ```  
  
## <a name="see-also"></a>См. также
[Общие сведения о данных N-уровневых приложениях](../data-tools/n-tier-data-applications-overview.md)   
[Добавление кода для наборов данных в n уровневых приложениях](../data-tools/add-code-to-datasets-in-n-tier-applications.md)   
[Создайте и настройте адаптеры таблиц TableAdapter](create-and-configure-tableadapters.md)   
[Общие сведения о иерархическое обновление](hierarchical-update.md)   

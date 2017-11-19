---
title: "Добавление кода для наборов данных в n уровневых приложениях | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: n-tier applications, extending datasets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
caps.latest.revision: "20"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 26dd5500f50b185c31809d9882e03e56541a567a
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>Добавление кода для наборов данных в n уровневых приложениях
Можно расширить функциональные возможности набора данных путем создания файла разделяемого класса для набора данных и добавления к нему кода (вместо добавления кода в *DatasetName*. Dataset.Designer-файл). Разделяемые классы позволяют коду для определенного класса разделяться между несколькими физическими файлами. Дополнительные сведения см. в разделе [частичного](/dotnet/visual-basic/language-reference/modifiers/partial) или [разделяемые классы и методы](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods).  
  
Код, который определяет набор данных создается каждый раз изменений в определение набора данных (в типизированный набор данных). Этот код также создается при внесении изменений во время выполнения мастеров, изменяющих конфигурацию набора данных. Чтобы предотвратить удаление во время повторного формирования набора данных в коде, добавьте код в файл разделяемого класса набора данных.  
  
По умолчанию после разделения кода адаптера таблицы и набора данных получается отдельные файлы классов в каждом проекте. Исходный проект содержит файл с именем *DatasetName*. Designer.vb (или *DatasetName*. Designer.cs), содержащий код адаптера таблицы. Проект, который назначен в **Dataset проекта** свойство имеет файл с именем *DatasetName*. DataSet.Designer.vb (или *DatasetName*. DataSet.Designer.cs). Этот файл содержит код набора данных.  
  
> [!NOTE]
>  При разделении наборов данных и адаптеров таблиц (установив **DataSet проекта** свойства), существующие разделяемые классы наборов данных в проекте не перемещаются автоматически. Существующие разделяемые классы наборов данных должны быть вручную перемещены в проект набора данных.  
  
> [!NOTE]
>  При проверке кода должен быть добавлен, типизированный набор данных предоставляет функциональные возможности для создания <xref:System.Data.DataTable.ColumnChanging> и <xref:System.Data.DataTable.RowChanging> обработчики событий. Дополнительные сведения см. в разделе [Добавление проверки в n уровневом наборе данных](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
## <a name="to-add-code-to-datasets-in-n-tier-applications"></a>Добавление кода для наборов данных в многоуровневых приложениях  
  
1.  Найдите проект, который содержит файл с расширением XSD. 
  
2.  Выберите **.xsd** файл, чтобы открыть набор данных.  
  
3.  Щелкните правой кнопкой мыши таблицу данных, к которому нужно добавить код (имя таблицы в строке заголовка), а затем выберите **Просмотр кода**.  
  
     Разделяемый класс создается и открывается в редакторе кода.  
  
4.  Добавьте код в объявление разделяемого класса.  
  
     Ниже приведен пример, куда нужно добавить код для CustomersDataTable в NorthwindDataSet.  
  
    ```vb  
    Partial Public Class CustomersDataTable  
        ' Add code here to add functionality   
        ' to the CustomersDataTable.  
    End Class  
    ```    
    ```csharp  
    partial class CustomersDataTable  
    {  
        // Add code here to add functionality  
        // to the CustomersDataTable.  
    }  
    ```  
  
## <a name="see-also"></a>См. также
[Общие сведения о данных N-уровневых приложениях](../data-tools/n-tier-data-applications-overview.md)   
[Добавление кода для объектов TableAdapter в многоуровневых приложениях](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)  
[Создайте и настройте адаптеры таблиц TableAdapter](create-and-configure-tableadapters.md)  
[Общие сведения о иерархическое обновление](hierarchical-update.md)     
[Инструменты для работы с наборами данных в Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)
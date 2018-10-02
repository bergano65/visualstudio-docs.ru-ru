---
title: Добавление кода для наборов данных в n уровневых приложениях | Документация Майкрософт
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
- n-tier applications, extending datasets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 74786c7fc32057881afd05b62dd2f48dfddbaffe
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561045"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>Добавление кода для наборов данных в n-уровневых приложениях
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Добавление кода для наборов данных в n уровневых приложениях](https://docs.microsoft.com/visualstudio/data-tools/add-code-to-datasets-in-n-tier-applications).  
  
  
Можно расширить функциональные возможности набора данных путем создания файла разделяемого класса для набора данных и добавления к нему кода (вместо добавления кода к *DatasetName*. Файл Dataset.Designer). Разделяемые классы позволяют коду для конкретного класса необходимо распределить между несколькими физическими файлами. Дополнительные сведения см. в разделе [частичного](http://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) или [разделяемые классы и методы](http://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1).  
  
 Код, который определяет набор данных создается каждый раз при внесении изменений в определение набора данных (в [Создание и изменение типизированных наборов DataSet](../data-tools/creating-and-editing-typed-datasets.md)). Этот код также создается при внесении изменений во время выполнения мастеров, изменяющих конфигурацию набора данных. Чтобы ваш код удалилась во время повторного формирования набора данных, добавьте код в файл разделяемого класса набора данных.  
  
 По умолчанию, после разделения набора данных и `TableAdapter` кода, результат — это отдельные файлы классов в каждом проекте. Исходный проект имеет filenamed *DatasetName*. Designer.vb (или *DatasetName*. Designer.cs), содержащий `TableAdapter` кода. Проект, который определен в **проект Dataset** свойство имеет файл с именем *DatasetName*. DataSet.Designer.vb (или *DatasetName*. DataSet.Designer.cs). Этот файл содержит код набора данных.  
  
> [!NOTE]
>  При разделении наборов данных и `TableAdapter`s (задавая **проект DataSet** свойство), существующие разделяемые классы наборов данных в проекте не перемещаются автоматически. Существующие разделяемые классы наборов данных должны быть вручную перемещены в проект набора данных.  
  
> [!NOTE]
>  При проверке кода должен быть добавлен, [Создание и изменение типизированных наборов DataSet](../data-tools/creating-and-editing-typed-datasets.md)предоставляет функциональность для создания <xref:System.Data.DataTable.ColumnChanging> и <xref:System.Data.DataTable.RowChanging> обработчики событий. Дополнительные сведения см. в разделе [Добавление проверки в n уровневом наборе данных](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
### <a name="to-add-code-to-datasets-in-n-tier-applications"></a>Добавление кода для наборов данных в n уровневых приложениях  
  
1.  Найдите проект, содержащий XSD-файл ( [Создание и изменение типизированных наборов DataSet](../data-tools/creating-and-editing-typed-datasets.md)).  
  
2.  Выберите **.xsd** файл, чтобы открыть [Создание и изменение типизированных наборов DataSet](../data-tools/creating-and-editing-typed-datasets.md).  
  
3.  Щелкните правой кнопкой мыши таблицу данных, к которому требуется добавить код (имя таблицы в заголовке окна) и thenselect**Просмотр кода**.  
  
     Разделяемый класс создается и открывается в редакторе кода.  
  
4.  Добавьте код в объявление разделяемого класса.  
  
     В следующем примере показано место добавления кода к CustomersDataTable в NorthwindDataSet:  
  
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
 [Общие сведения о данных в N-уровневых приложениях](../data-tools/n-tier-data-applications-overview.md)   
 [Добавление кода для объектов TableAdapter в многоуровневых приложениях](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)   
 [Адаптеры таблиц](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)   
 [Общие сведения о компоненте TableAdapterManager](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)   
 [Общие сведения о иерархическое обновление](http://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)   
 [Создание приложений данных](../data-tools/creating-data-applications.md)   
 [Инструменты для работы с наборами данных в Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)


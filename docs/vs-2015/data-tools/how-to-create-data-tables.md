---
title: 'Практическое: создание таблиц данных | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Microsoft.VSDesigner.DataSource.DesignTable
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio], creating data tables
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
ms.assetid: 0e8bf4c4-3d05-4b20-9926-9d29914b26ed
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 596c2760e100bc45eefdde10743b3d9b45490b91
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47569989"
---
# <a name="how-to-create-data-tables"></a>Практическое руководство. Создание таблиц данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Данные могут храниться в памяти в <xref:System.Data.DataTable> объектов. (Наборы данных, состоящего из <xref:System.Data.DataTable> объекты.) Обычно создание новых таблиц данных с использованием адаптеров таблиц TableAdapter [мастер настройки адаптера таблицы](http://msdn.microsoft.com/library/3a373dd9-7b34-4d3c-a48b-69414512bac8) или путем перетаскивания объектов базы данных из **обозревателя серверов** на **конструктор наборов данных** .  
  
 Данные таблицы создаются в результате, при создании нового адаптера таблицы в [мастер настройки источника данных](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) , но могут быть созданы и независимо друг от друга. Создать автономную таблицу данных, перетащив <xref:System.Data.DataTable> объекта из **набора данных** вкладке **элементов** на **конструктор наборов данных**.  
  
> [!NOTE]
>  Создание таблиц данных программными средствами, см. в разделе [создание объекта DataTable](http://msdn.microsoft.com/library/eecf9d78-60e3-4fdc-8de0-e56c13a89414).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="creating-a-datatable-with-tableadapter"></a>Создание таблицы данных с помощью адаптера таблицы  
 Таблицы данных с помощью адаптеров таблиц включают методы, которые заполнения таблицы данными и обратной записи изменения в базу данных. Создание адаптеров таблиц TableAdapter, запустив **мастер настройки адаптера таблицы** или путем перетаскивания объектов базы данных из **обозревателя серверов** на **конструктор наборов данных**.  
  
#### <a name="to-create-a-new-data-table-with-tableadapter"></a>Чтобы создать новую таблицу данных с помощью адаптера таблицы  
  
1.  Откройте набор данных в **конструктор наборов данных**. Сведения см. в разделе [как: Открытие набора данных в конструкторе наборов данных](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Перетащите **TableAdapter** из **набора данных** вкладке **элементов** на **конструктор наборов данных**.  
  
     **Мастер настройки адаптера таблицы** открывает.  
  
3.  Завершите работу мастера. Дополнительные сведения см. в разделе [мастер настройки адаптера таблицы](http://msdn.microsoft.com/library/3a373dd9-7b34-4d3c-a48b-69414512bac8)  
  
#### <a name="to-create-a-new-data-table-with-a-tableadapter-from-server-explorer"></a>Чтобы создать новую таблицу данных с помощью адаптера таблицы с помощью обозревателя сервера  
  
1.  Откройте набор данных в **конструктор источников данных**.  
  
2.  Перетащите объект базы данных (например, таблицу) из **обозревателя серверов** на **конструктор наборов данных**.  
  
## <a name="creating-a-standalone-datatable"></a>Создание автономной таблицы данных  
 Автономные таблицы должны иметь `Fill` реализовать логику для заполнения данными. Сведения о заполнении автономных таблиц данных, см. в разделе [заполнение набора данных из объекта DataAdapter](http://msdn.microsoft.com/library/3fa0ac7d-e266-4954-bfac-3fbe2f913153).  
  
#### <a name="to-create-a-new-stand-alone-data-table"></a>Чтобы создать новый автономной таблицы данных  
  
1.  Откройте набор данных в **конструктор наборов данных**.  
  
2.  Перетащите <xref:System.Data.DataTable> из **набора данных** вкладке **элементов** на **конструктор наборов данных**.  
  
3.  Добавьте столбцы для определения таблицы данных. Дополнительные сведения см. в разделе [как: Добавление столбцов к таблице DataTable](http://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df).  
  
## <a name="see-also"></a>См. также  
 <xref:System.Data.DataTable>   
 [Примеры работы с данными](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Пошаговое руководство: Отображение данных в форме Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Общие сведения о TableAdapter](../data-tools/tableadapter-overview.md)   
 [Создание и изменение типизированных наборов данных](../data-tools/creating-and-editing-typed-datasets.md)   
 [Добавление новых источников данных](../data-tools/add-new-data-sources.md)   
 [Окно источников данных](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)   
 [Практическое руководство. Подключение к данным в базе данных](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Проверка данных](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)
---
title: Расширения функциональных возможностей адаптера таблицы | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Visual Studio], TableAdapters
- data [Visual Studio], extending TableAdapters
- TableAdapters, adding functionality
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: d163461f559432752815d2f1e1fec103d93a84ec
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>Расширения функциональных возможностей адаптера таблицы
Можно расширить функциональные возможности адаптера таблицы путем добавления кода в файл разделяемого класса адаптера таблицы.  
  
 Код, определяющий адаптер таблицы заново после внесения изменений в адаптер таблицы в **конструктора наборов данных**, или когда мастер изменяет конфигурацию адаптера таблицы. Чтобы предотвратить удаление во время повторного формирования адаптера таблицы в коде, добавьте код в файл разделяемого класса адаптера таблицы.  
  
 Разделяемые классы позволяют коду определенного класса разделяться между несколькими физическими файлами. Дополнительные сведения см. в разделе [частичного](/dotnet/visual-basic/language-reference/modifiers/partial) или [partial (тип)](/dotnet/csharp/language-reference/keywords/partial-type).  
  
## <a name="locate-tableadapters-in-code"></a>Найдите в коде адаптеры таблиц TableAdapter  
 Если адаптеры таблиц создаются с помощью **конструктора наборов данных**, созданные классы адаптеров таблиц не вложенные классы <xref:System.Data.DataSet>. Адаптеры таблиц TableAdapter находятся в пространстве имен на основе имени связанного набора данных адаптера таблицы. Например, если приложение содержит набор данных с именем `HRDataSet`, адаптеры таблиц должны быть расположены в `HRDataSetTableAdapters` пространства имен. (Соглашение об именовании имеет следующую структуру: *DatasetName* + `TableAdapters`).  
  
 В следующем примере предполагается адаптера таблицы с именем `CustomersTableAdapter`находится в проекте с `NorthwindDataSet`.  
  
#### <a name="to-create-a-partial-class-for-a-tableadapter"></a>Для создания разделяемого класса для адаптера таблицы  
  
1.  Добавьте новый класс в проект, выбрав пункты **проекта** , выберите в меню **Добавление класса**.  
  
2.  Присвойте классу имя `CustomersTableAdapterExtended`.  
  
3.  Выберите **добавить**.  
  
4.  Замените код правильное пространство имен и именем разделяемого класса для проекта следующим образом:  
  
     [!code-csharp[VbRaddataTableAdapters#2](../data-tools/codesnippet/CSharp/extend-the-functionality-of-a-tableadapter_1.cs)]
     [!code-vb[VbRaddataTableAdapters#2](../data-tools/codesnippet/VisualBasic/extend-the-functionality-of-a-tableadapter_1.vb)]  
  
## <a name="see-also"></a>См. также  
 [Заполнение наборов данных с помощью адаптера таблицы](../data-tools/fill-datasets-by-using-tableadapters.md)
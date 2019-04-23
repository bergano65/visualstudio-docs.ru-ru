---
title: Расширения функциональных возможностей адаптера таблицы | Документация Майкрософт
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
- data [Visual Studio], TableAdapters
- data [Visual Studio], extending TableAdapters
- TableAdapters, adding functionality
ms.assetid: 418249c8-c7f3-47ef-a94c-744cb6fe6aaf
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: db6ea3e2b19b655c3a1ec8dedf60409b8706f3cd
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60059036"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>Расширение функциональных возможностей адаптера таблицы TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно расширить функциональные возможности адаптера таблицы, добавив код в файл разделяемого класса TableAdapter.  
  
 Код, который определяет TableAdapter генерируется при внесении изменений в адаптер таблицы в **конструктор наборов данных**, или когда мастер изменяет конфигурацию адаптера таблицы. Чтобы предотвратить удаление во время повторного формирования адаптера таблицы в коде, добавьте код в файл разделяемого класса TableAdapter.  
  
 Разделяемые классы позволяют коду для конкретного класса необходимо распределить между несколькими физическими файлами. Дополнительные сведения см. в разделе [частичного](http://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) или [partial (тип)](http://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334).  
  
## <a name="locate-tableadapters-in-code"></a>Найдите адаптеры таблицы в коде  
 Если адаптеры таблиц создаются с помощью **конструктор наборов данных**, создаваемых классов TableAdapter не вложенные классы <xref:System.Data.DataSet>. Адаптеры таблиц находятся в пространстве имен, на основе имени связанного набора данных TableAdapter. Например, если приложение содержит набор данных с именем `HRDataSet`, адаптеры таблиц будут расположены в `HRDataSetTableAdapters` пространства имен. (Соглашение об именовании соответствует следующему шаблону: *DatasetName* + `TableAdapters`).  
  
 В следующем примере предполагается адаптера таблицы с именем `CustomersTableAdapter`находится в проекте с `NorthwindDataSet`.  
  
#### <a name="to-create-a-partial-class-for-a-tableadapter"></a>Для создания разделяемого класса для адаптера таблицы  
  
1. Добавить новый класс в проект, выбрав **проекта** меню и выбрав**Добавление класса**.  
  
2. Присвойте классу имя `CustomersTableAdapterExtended`.  
  
3. Нажмите **Добавить**.  
  
4. Замените код с правильно заданным пространством имен и именем разделяемого класса для вашего проекта следующим образом:  
  
     [!code-csharp[VbRaddataTableAdapters#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/CustomersTableAdapterExtended.cs#2)]
     [!code-vb[VbRaddataTableAdapters#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/CustomersTableAdapterExtended.vb#2)]  
  
## <a name="see-also"></a>См. также  
 [Заполнение наборов данных с помощью адаптера таблицы](../data-tools/fill-datasets-by-using-tableadapters.md)

---
title: Расширение функциональных возможностей адаптера таблицы | Документация Майкрософт
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 19367f812a87d6aa585e123100f1d08144c57ff9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672362"
---
# <a name="extend-the-functionality-of-a-tableadapter"></a>Расширение функциональных возможностей адаптера таблицы TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Функциональные возможности TableAdapter можно расширить, добавив код в файл разделяемого класса TableAdapter.

 Код, определяющий TableAdapter, создается повторно при внесении любых изменений в TableAdapter в **Конструктор наборов данных**или когда мастер изменяет конфигурацию адаптера таблицы. Чтобы предотвратить удаление кода во время повторного создания адаптера таблицы TableAdapter, добавьте код в файл разделяемого класса TableAdapter.

 Разделяемые классы позволяют разделить код для определенного класса между несколькими физическими файлами. Дополнительные сведения см. в разделе [partial](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) или [partial (Type)](https://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334).

## <a name="locate-tableadapters-in-code"></a>Обнаружение адаптеров таблиц в коде
 Хотя адаптеры таблиц разработаны с **Конструктор наборов данных**, создаваемые классы TableAdapter не являются вложенными классами <xref:System.Data.DataSet>. Адаптеры таблиц расположены в пространстве имен на основе имени связанного с TableAdapter набора данных. Например, если приложение содержит набор данных с именем `HRDataSet`, адаптеры таблиц будут расположены в пространстве имен `HRDataSetTableAdapters`. (Соглашение об именовании соответствует следующему шаблону: *DatasetName* + `TableAdapters`).

 В следующем примере предполагается, что TableAdapter с именем `CustomersTableAdapter`is в проекте с `NorthwindDataSet`.

#### <a name="to-create-a-partial-class-for-a-tableadapter"></a>Создание разделяемого класса для TableAdapter

1. Добавьте новый класс в проект, выбрав в меню **проект** пункт**Добавить класс**.

2. Присвойте классу имя `CustomersTableAdapterExtended`.

3. Нажмите **Добавить**.

4. Замените код правильным пространством имен и именем разделяемого класса для проекта следующим образом:

     [!code-csharp[VbRaddataTableAdapters#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/CustomersTableAdapterExtended.cs#2)]
     [!code-vb[VbRaddataTableAdapters#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/CustomersTableAdapterExtended.vb#2)]

## <a name="see-also"></a>См. также раздел
 [Заполнение наборов данных с помощью адаптера таблицы](../data-tools/fill-datasets-by-using-tableadapters.md)

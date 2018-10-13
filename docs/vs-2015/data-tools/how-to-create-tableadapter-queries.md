---
title: 'Практическое: создание запросов TableAdapter | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
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
- TableAdapters, creating queries
- queries [Visual Studio], creating
- data [Visual Studio], TableAdapter queries
- queries [Visual Studio], TableAdapters
ms.assetid: df0cf4a5-e9cc-4de6-8b94-ce74fb7b2452
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: c4b800bcb70e41e1d80bf9a0a37d72f08f78c7a6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49195550"
---
# <a name="how-to-create-tableadapter-queries"></a>Практическое руководство. Создание запросов TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Запросы TableAdapter, инструкции SQL или хранимые процедуры, которые приложение может выполняться в базе данных.  
  
 Добавьте столько запросов в адаптер таблицы вашему приложению. Запросы адаптера таблицы отображаются в виде методы адаптера таблицы. При создании запроса с именем `FillByCity` , принимающий параметр, который представляет значение города, запрос будет добавлен в адаптер таблицы. Он добавляется как типизированный метод, который принимает правильный тип параметра в качестве аргумента — в данном случае строка, представляющая значение города. Вызов запроса адаптера таблицы так же, как и любой метод для любого объекта. Например, следующий код выполняет `FillByCity` запроса и заполняет `Customers` таблицу со всех клиентов со значением города `Seattle`:  
  
 [!code-csharp[VbRaddataTableAdapters#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Form1.cs#1)]
 [!code-vb[VbRaddataTableAdapters#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Form1.vb#1)]  
  
 Запросы адаптера таблицы можно заполнить таблицу данных (`Fill` и `FillBy` запросов) или возвращать новые таблицы данных заполняется данными, возвращенных запросом (`GetData` и `GetDataBy` запросов).  
  
 Можно добавить запросы для существующих TableAdapter, запустив [редактирования TableAdapters](../data-tools/editing-tableadapters.md). (Щелкните правой кнопкой мыши TableAdapter и выберите **добавить запрос**.)  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="create-a-query-in-the-dataset-designer"></a>Создание запроса в конструкторе наборов данных  
  
#### <a name="to-add-a-query-to-a-tableadapter-in-the-dataset-designer"></a>Добавление запроса адаптера таблицы в конструкторе наборов данных  
  
1.  Откройте набор данных в **конструктор наборов данных**. Дополнительные сведения см. в разделе [как: Открытие набора данных в конструкторе наборов данных](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Щелкните правой кнопкой мыши нужный TableAdapter и выберите **добавить запрос**.  
  
     - или -  
  
3.  Перетащите **запроса** из **набора данных** вкладке **элементов** в таблицу в конструкторе.  
  
     **Мастер настройки запроса TableAdapter** открывает.  
  
4.  Завершите работу мастера; запрос добавляется в адаптер таблицы.  
  
## <a name="create-a-query-directly-on-a-form-in-your-windows-application"></a>Создать запрос непосредственно на форме в приложении Windows  
 Если у вас экземпляр адаптера таблицы в форму можно добавить запрос, используя [Построитель условий поиска-диалоговое окно](http://msdn.microsoft.com/library/0b306b92-f35e-45ef-a4be-3f653cd00c3d), который добавляет <xref:System.Windows.Forms.ToolStrip> элемента управления в форму, которая принимает входные параметры, необходимые для запроса, а также Чтобы выполнить запрос.  
  
#### <a name="to-add-a-query-to-a-tableadapter-using-the-search-criteria-dialog-box"></a>Добавление запроса адаптера таблицы с помощью диалогового окна критерии поиска  
  
1.  Выберите адаптер таблицы в области компонентов.  
  
2.  Щелкните смарт-тег TableAdapter и выберите **добавить запрос**.  
  
3.  Заполните диалоговое окно, и запрос будет добавлен в адаптер таблицы. Дополнительные сведения см. в разделе [Построитель условий поиска-диалоговое окно](http://msdn.microsoft.com/library/0b306b92-f35e-45ef-a4be-3f653cd00c3d).  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о TableAdapter](../data-tools/tableadapter-overview.md)   
 [Практическое: изменение запросов TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Создание и изменение типизированных наборов данных](../data-tools/creating-and-editing-typed-datasets.md)   
 [Добавление новых источников данных](../data-tools/add-new-data-sources.md)   
 [Практическое руководство. Подключение к данным в базе данных](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Проверка данных](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Практическое: навигация по набору данных с помощью элемента управления BindingNavigator в Windows Forms](http://msdn.microsoft.com/library/0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb)   
 [Пошаговое руководство: Отображение данных в форме Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Пошаговое руководство. Создание адаптера таблицы с несколькими запросами](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)
---
title: 'Практическое: Добавление глобальных запросов адаптера таблицы | Документация Майкрософт'
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
- global functions, datasets
- scalar functions, datasets
- TableAdapters, global queries
- data [Visual Studio], TableAdapters
- datasets [Visual Basic], scalar functions
- TableAdapter Query Configuration Wizard
- datasets [Visual Basic], global functions
- TableAdapter queries
- queries [Visual Studio], TableAdapters
ms.assetid: 4abffd6b-2e9f-4ef3-99b2-6e9ae4ad4679
caps.latest.revision: 13
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 681fea494557e555c745d33c07c4e2c25cfe0f88
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47560931"
---
# <a name="how-to-add-global-queries-to-a-tableadapter"></a>Практическое: Добавление глобальных запросов адаптера таблицы
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Глобальные запросы* являются SQL-запросы, которые возвращают одно (скалярное) значение или нет значения. Как правило глобальные функции выполнения операций базы данных, например операции вставки, обновления, удаления и сбор данных, таких как возврат числа клиентов в таблице или общие платежи для всех элементов в определенном порядке.  
  
 Добавление глобальных запросов, выполнив **мастер настройки запроса TableAdapter** изнутри **конструктор наборов данных**.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-add-a-global-query-to-a-dataset"></a>Чтобы добавить глобальный запрос к набору данных  
  
1.  Откройте набор данных в **конструктор наборов данных**. Дополнительные сведения см. в разделе [как: Открытие набора данных в конструкторе наборов данных](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Перетащите **запроса** из **набора данных** вкладке **элементов** фигуру на пустую область **конструктор наборов данных**.  
  
     [Редактирования TableAdapters](../data-tools/editing-tableadapters.md) открывает.  
  
3.  Выберите соединение для запроса для использования. Можно выбрать один из списка или создайте новое соединение. При создании нового соединения, имеется возможность сохранять его в файле конфигурации приложения. Дополнительные сведения см. в разделе [как: сохранение и изменение строк подключения](~/E:/Repos/visualstudio-docs-pr/docs/data-tools/how-to-save-and-edit-connection-strings.md).  
  
4.  Выберите, следует ли использовать инструкции SQL или хранимые процедуры.  
  
5.  Выберите хранимую процедуру для использования или на **Выбор типа запроса** страницы мастера, выберите тип запроса и нажмите кнопку **Далее**.  
  
6.  Указать запрос, который выполняет требуемую задачу, например, `SELECT COUNT(*) AS CustomerCount FROM Customers`.  
  
    > [!NOTE]
    >  При перетаскивании запроса непосредственно на **конструктор наборов данных** создает метод, который будет возвращать только скалярное значение (одно). Хотя запрос или хранимая процедура может возвращать более одного значения, созданный мастером метод будет возвращать только одно значение. Например запрос может возвратить первый столбец первой строки возвращаемых данных.  
  
7.  Завершите работу мастера; запрос будет добавлен к **конструктор наборов данных**. Сведения о выполнении запроса см. в разделе [как: выполнение запросов TableAdapter](http://msdn.microsoft.com/library/c7518855-f896-41c1-b3de-1a8116280593).  
  
## <a name="see-also"></a>См. также  
 [Создание и настройка адаптеров таблиц](../data-tools/create-and-configure-tableadapters.md)   
 [Практическое: создание запросов TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)   
 [Привязка элементов управления Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Общие сведения о TableAdapter](../data-tools/tableadapter-overview.md)   
 [Создание и изменение типизированных наборов данных](../data-tools/creating-and-editing-typed-datasets.md)   
 [Добавление новых источников данных](../data-tools/add-new-data-sources.md)   
 [Практическое руководство. Подключение к данным в базе данных](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Проверка данных](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Практическое: навигация по набору данных с помощью элемента управления BindingNavigator в Windows Forms](http://msdn.microsoft.com/library/0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb)   
 [Пошаговое руководство. Отображение данных на форме в приложении Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)
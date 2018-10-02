---
title: Visual Studio data tools для .NET | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 759aaa1f6860d6b8e95aeaae786532ff406acbb4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47561157"
---
# <a name="visual-studio-data-tools-for-net"></a>Visual Studio Data Tools для .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio и .NET Framework вместе предоставляют обширный API и поддержка средств для подключения к базам данных, моделирование данных в памяти и отображения данных в пользовательском интерфейсе.  Классы .NET Framework, которые предоставляют функциональные возможности доступа к данным, называются [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx). ADO.NET, вместе с данными, инструменты Visual Studio, изначально разрабатывалась в первую очередь для поддержки реляционных баз данных и XML. Наши дни многие поставщики базы данных NoSQL или сторонних разработчиков, предлагают поставщиков ADO.NET.  
  
 Visual Studio 2015 с обновлением 2 включает в себя последние обновления [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx), обеспечивающие поддержку последних функций Azure [базы данных SQL](https://azure.microsoft.com/en-us/services/sql-database/) и [SQL Server 2016](https://www.microsoft.com/en-us/server-cloud/products/sql-server-2016/). [.NET core](https://www.dotnetfoundation.org/netcore) поддерживает ADO.NET, за исключением наборов данных и связанных типов. Если вы ориентируетесь на .NET Core и требовать уровень объектно реляционного сопоставления (ORM), используйте [Entity Framework Core](https://msdn.microsoft.com/data/ef.aspx).  
  
 В примере ниже показан упрощенное представление базовая архитектура:  
  
 ![Архитектура ADO.NET](../data-tools/media/raddata-ado-net-architecture-diagram.png "raddata схема архитектуры ADO.NET")  
  
 Типичный рабочий процесс такова:  
  
1.  Установите на локальном компьютере разработки или тестовой базы данных. См. в разделе [установка систем баз данных, средства и примеры](../data-tools/installing-database-systems-tools-and-samples.md). Если вы используете службу Azure данных, этот шаг необязателен.  
  
2.  Проверьте подключение к базе данных (или службы или локального файла) в Visual Studio. См. в разделе [Добавление новых подключений](../data-tools/add-new-connections.md).  
  
3.  (Необязательно) Средства создания и настройки новой модели. Модели, на платформе Entity Framework — рекомендации по умолчанию для новых приложений. Модели, выбрать любой из них используется, является, приложение взаимодействует с источником данных. Модель логически располагается между базы данных или службой и приложением.  См. в разделе [добавляются новые источники данных](../data-tools/add-new-data-sources.md).  
  
4.  Перетащите источник данных из **источников данных** в рабочую область конструктора Windows Forms, ASP.NET или Windows Presentation Foundation для создания кода привязки данных, который будет отображать данные для пользователя, можно указать как. См. в разделе [привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
5.  Добавление пользовательского кода для задач, таких как бизнес-правила, поиска и проверки данных, либо пользоваться преимуществами пользовательские функции, которые предоставляет основной базе данных.  
  
 Можно пропустить шаг 3 и программировать приложения .NET для передачи команд непосредственно в базу данных, а не с помощью модели. В этом случае вы найдете здесь документацию: [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx). Обратите внимание на то, что по-прежнему можно использовать мастер настройки источника данных и конструкторы для формирования кода привязки данных при заполнении собственных объектов в памяти, а затем выполнить привязку данных элементов управления пользовательского интерфейса к этим объектам.  
  
## <a name="in-this-section"></a>Содержание раздела  
  
-   [Создание простого приложения для работы с данными с помощью ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md)  
  
-   [Добавление новых подключений](../data-tools/add-new-connections.md)  
  
-   [Добавление новых источников данных](../data-tools/add-new-data-sources.md)  
  
-   [Средства работы с моделью EDM в Visual Studio](../data-tools/entity-data-model-tools-in-visual-studio.md)  
  
-   [Инструменты для работы с наборами данных в Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)  
  
-   [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)  
  
-   [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)  
  
-   [Дополнительные ресурсы для устранения неполадок, связанных с ошибками доступа к данным](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)  
  
-   [Службы Windows Communication Foundation и службы данных WCF в Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)  
  
-   [Создание баз данных и приложений уровня данных, а также управление ими в Visual Studio](../data-tools/creating-and-managing-databases-and-data-tier-applications-in-visual-studio.md)  
  
-   [Дополнительные ресурсы для устранения неполадок, связанных с ошибками доступа к данным](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)  
  
## <a name="see-also"></a>См. также  
 [Доступ к данным в Visual Studio](../data-tools/accessing-data-in-visual-studio.md)








---
title: Visual Studio Data Tools для .NET | Документация Майкрософт
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9d591595c65f00e0198ded9492ae0b8399e363e5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670103"
---
# <a name="visual-studio-data-tools-for-net"></a>Visual Studio Data Tools для .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio и .NET Framework предоставляют обширную поддержку API и средств для подключения к базам данных, моделирования данных в памяти и отображения данных в пользовательском интерфейсе.  .NET Framework классы, предоставляющие функциональные возможности доступа к данным, называются [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx). ADO.NET, а также инструменты для работы с данными в Visual Studio изначально разрабатывались в основном для поддержки реляционных баз данных и XML. Эти дни, многие поставщики баз данных NoSQL или сторонние лица предлагают поставщиков ADO.NET.

 Visual Studio 2015 с обновлением 2 включает последние обновления [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx), которые обеспечивают поддержку новейших функций в [базе данных SQL](https://azure.microsoft.com/services/sql-database/) Azure и [SQL Server 2016](https://www.microsoft.com/sql-server/sql-server-2016). [.NET Core](https://www.dotnetfoundation.org/projects?searchquery=dotnet+core&type=project) поддерживает ADO.NET, за исключением наборов данных и связанных типов. Если вы нацелены на .NET Core и требуется уровень объектно-реляционного сопоставления (ORM), используйте [Entity Framework Core](https://msdn.microsoft.com/data/ef.aspx).

 На следующей диаграмме показано упрощенное представление базовой архитектуры.

 ![Архитектура ADO.NET](../data-tools/media/raddata-ado-net-architecture-diagram.png "Схема архитектуры раддата ADO.NET")

 Типичный рабочий процесс:

1. Установите базу данных для разработки или тестирования на локальном компьютере. См. раздел [Установка систем баз данных, средств и примеров](../data-tools/installing-database-systems-tools-and-samples.md). Если вы используете службу данных Azure, этот шаг не является обязательным.

2. Проверьте подключение к базе данных (или службе или локальному файлу) в Visual Studio. См. раздел [Добавление новых соединений](../data-tools/add-new-connections.md).

3. Используемых Используйте средства для создания и настройки новой модели. Модели, основанные на Entity Framework, являются рекомендацией по умолчанию для новых приложений. Используемая модель — это источник данных, с которым взаимодействует приложение. Модель логически располагается между базой данных или службой и приложением.  См. раздел [Добавление новых источников данных](../data-tools/add-new-data-sources.md).

4. Перетащите источник данных из окна **Источники данных** на область конструктора Windows Forms, ASP.NET или Windows Presentation Foundation, чтобы создать код привязки данных, который будет отображать данные пользователю в указанном вами виде. См. раздел [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

5. Добавьте пользовательский код для таких объектов, как бизнес-правила, Поиск и проверка данных, или воспользуйтесь преимуществами пользовательских функций, предоставляемых базовой базой данных.

   Можно пропустить шаг 3 и программировать приложение .NET для выполнения команд непосредственно в базе данных, а не использовать модель. В этом случае вы найдете здесь документацию: [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx). Обратите внимание, что по-прежнему можно использовать мастер настройки источника данных и конструкторы для создания кода привязки данных при заполнении собственных объектов в памяти, а затем привязывать к этим объектам элементы управления ИП привязки данных.

## <a name="in-this-section"></a>В данном разделе

- [Создание простого приложения для работы с данными с помощью ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md)

- [Добавление новых подключений](../data-tools/add-new-connections.md)

- [Добавление новых источников данных](../data-tools/add-new-data-sources.md)

- [Средства работы с моделью EDM в Visual Studio](../data-tools/entity-data-model-tools-in-visual-studio.md)

- [Инструменты для работы с наборами данных в Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)

- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)

- [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)

- [Дополнительные ресурсы для устранения неполадок, связанных с ошибками доступа к данным](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)

- [Службы Windows Communication Foundation и службы данных WCF в Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

- [Создание баз данных и приложений уровня данных, а также управление ими в Visual Studio](../data-tools/creating-and-managing-databases-and-data-tier-applications-in-visual-studio.md)

- [Дополнительные ресурсы для устранения неполадок, связанных с ошибками доступа к данным](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)

## <a name="see-also"></a>См. также раздел
 [Доступ к данным в Visual Studio](../data-tools/accessing-data-in-visual-studio.md)

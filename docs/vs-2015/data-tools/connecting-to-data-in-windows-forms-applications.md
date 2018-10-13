---
title: Подключение к данным в Windows Forms приложений | Документация Майкрософт
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- System.Data.SqlClient.SqlConnection
- System.Data.Odbc.OdbcConnection
- System.Data.OleDb.OleDbConnection
- System.Data.OracleClient.OracleConnection
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- connection objects, tools for working with
- OleDbConnection class, ADO.NET connection objects
- databases [Visual Studio], connecting to
- data adapters, connections
- connection pooling, ADO.NET connections
- connection strings [Visual Studio], ADO.NET
- connection objects, types of
- dynamic properties, ADO.NET connections
- connections, about connections
- data [Visual Studio], connecting
- design-time connections
- connections, design-time
- TableAdapters, connections
- connection objects
- SqlConnection class, ADO.NET connection objects
- connecting to databases, ADO.NET connections
- transactions, ADO.NET
- database connections [Visual Studio], ADO.NET
ms.assetid: 184cbd0d-3b26-418d-a11c-f9f8f004fbff
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: d8da35b32f3dd25bd7ed47b25f722c6b0aa21ac7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/12/2018
ms.locfileid: "49208953"
---
# <a name="connecting-to-data-in-windows-forms-applications"></a>Подключение к данным в приложениях Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] предоставляет средства для подключения вашего приложения к данным из множества разных источников, таких как базы данных, веб-службы и объекты. Если вы используете инструменты проектирования данных в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], вам часто не требуется явно создавать объект подключения для своей формы или своего компонента. Обычно объект подключения создается в результате выполнения одного из мастеров по работе с данными или перетаскивания объектов данных на форму. Для подключения приложения к данным в базе данных, веб-службы или объекта, выполните [мастер настройки источника данных](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) , выбрав **добавить новый источник данных** из [окна "Источники данных"](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992).  
  
 На следующей схеме показана стандартная последовательность операций для подключения к данным посредством выполнения запроса адаптера таблицы в целях получения данных и их отображения на форме в приложении Windows.  
  
 ![Поток данных в клиентском приложении](../data-tools/media/clientdatadiagram.gif "ClientDataDiagram")  
  
 В некоторых ситуациях объект подключения удобно создавать без использования инструментов проектирования данных. Сведения о создании подключений см. в разделе [подключение к источнику данных](http://msdn.microsoft.com/library/9abc3f92-1be3-4e1a-b360-762dc689650e).  
  
> [!NOTE]
>  Сведения о подключении веб-приложений к данным, см. в разделе [схема содержимого для доступа к данным ASP.NET](http://msdn.microsoft.com/en-us/f9219396-a0fa-481f-894d-e3d9c67d64f2).  
  
## <a name="walkthroughs-for-connecting-windows-forms-applications-to-data"></a>Пошаговые руководства по подключению приложений Windows Forms к данным  
 Следующие пошаговые руководства содержат описание процедур, связанных с подключением к данным в приложениях Windows Forms:  
  
-   [Пошаговое руководство: Подключение к данным в базе данных (Windows Forms)](http://msdn.microsoft.com/library/02d39aa6-8993-4602-be13-a13536af3d1c)  
  
-   [Пошаговое руководство. Подключение к данным в локальном файле базе данных (Windows Forms)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)  
  
-   [Пошаговое руководство: Подключение к данным в веб-службы (Windows Forms)](http://msdn.microsoft.com/library/079fb9b0-c733-40c1-acd1-d0d68834354d)  
  
-   [Пошаговое руководство: Подключение к данным в объектах (Windows Forms)](http://msdn.microsoft.com/library/21a7fba2-b38b-4726-8cbe-d22154b75a05)  
  
-   [Подключение к данным в базе данных Access (Windows Forms)](../data-tools/connect-to-data-in-an-access-database-windows-forms.md)  
  
## <a name="creating-connections"></a>Создание подключений  
 В [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], подключения настраиваются с помощью **Добавить/изменить подключение** диалоговое окно. **Добавить подключение** диалоговое окно отображается при изменении или создании подключений в одном из мастеров данных или [Server Explorer/Database Explorer](http://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d) или при изменении свойств подключения в **свойства** окна.  
  
 Подключения к данным настраиваются автоматически при выполнении одного из следующих действий.  
  
|Действие|Описание|  
|------------|-----------------|  
|Запустите [мастера настройки источника данных](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).|Подключения настраиваются при выборе пути базы данных в **мастер настройки источника данных**. Дополнительные сведения см. в разделе [How to: Connect to Data in a Database](../data-tools/how-to-connect-to-data-in-a-database.md).|  
|Запустите [мастер настройки адаптера таблицы](http://msdn.microsoft.com/library/3a373dd9-7b34-4d3c-a48b-69414512bac8).|Подключения создаются в **мастер настройки адаптера таблицы**. Дополнительные сведения см. в разделе [Создание и настройка адаптеров таблиц](../data-tools/create-and-configure-tableadapters.md).|  
|Запустите [Правка адаптеров таблиц](../data-tools/editing-tableadapters.md).|Подключения создаются в **мастер настройки запроса TableAdapter**. Дополнительные сведения см. в разделе [как: создание запросов TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).|  
|Перетащите элементы из [окна "Источники данных"](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) на форму или [конструктор компонентов](http://msdn.microsoft.com/library/61a3a450-5b15-465e-bd9a-72a6c8c2b282).|Объекты подключения создаются при перетаскивании элементов из **источников данных** окна на **конструктор Windows Forms** или **конструктор компонентов**. Дополнительные сведения см. в разделе [привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).|  
|Добавление новых подключений к данным [Server Explorer/Database Explorer](http://msdn.microsoft.com/library/4ea29b3b-bbb2-45e4-9082-eaf635c41c4d).|Подключения к данным в **Server Explorer/Database Explorer** отображаются в списке доступных подключений в мастерах работы с данными|  
  
## <a name="connection-strings"></a>Строки подключения  
 Строки подключения могут храниться в скомпилированном приложении или в файле конфигурации приложения. Дополнительные сведения см. в разделе [как: сохранение и изменение строк подключения](~/E:/Repos/visualstudio-docs-pr/docs/data-tools/how-to-save-and-edit-connection-strings.md).  
  
## <a name="connection-information-and-security"></a>Информация о подключении и безопасность  
 Поскольку открытие подключения связано с получением доступа к важному ресурсу — базе данных, часто при настройке подключения и работе с ним возникают проблемы безопасности.  
  
 Способ обеспечения безопасности приложения и доступа к источнику данных зависит от архитектуры системы. Например, в веб-приложении пользователи обычно получают анонимный доступ к службам IIS, и поэтому не предоставляют учетные данные безопасности. В этом случае ваше приложение хранит собственную информацию для входа и использует ее для открытия подключения и доступа к базе данных вместо сведений конкретного пользователя.  
  
> [!IMPORTANT]
>  Хранение сведений строки подключения, например пароля, может повлиять на безопасность приложений. Использование встроенных средств безопасности Windows — более безопасный способ управления доступом к базе данных. Дополнительные сведения см. в разделе [Защита сведений о подключении](http://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4).  
  
 В приложениях интрасети или многоуровневых приложениях вы можете воспользоваться преимуществом встроенных средств безопасности, доступных в Windows, службах IIS и SQL Server. При такой модели учетные данные аутентификации пользователя для локальной сети также используются для доступа к ресурсам базы данных, и в строке подключения не используется имя пользователя или пароль в явной форме. Обычно разрешения задаются на компьютере сервера базы данных посредством групп, поэтому вам не нужно задавать отдельные разрешения для каждого пользователя, который может получить доступ к базе данных. В такой модели вам вообще не нужно хранить сведения о входе для подключения, а дополнительные меры по обеспечению безопасности информации строк подключения не требуются.  
  
 Дополнительные сведения о безопасности см. в следующих разделах:  
  
-   [Защита приложений ADO.NET](http://msdn.microsoft.com/library/005a1d43-6ee5-471e-ad98-1d30a44d49d5)  
  
-   [Более безопасный доступ к файлам и данным в Windows Forms](http://msdn.microsoft.com/library/3cd3e55b-2f5e-40dd-835d-f50f7ce08967)  
  
## <a name="design-time-connections-in-server-explorerdatabase-explorer"></a>Подключения времени разработки в Обозревателе серверов/баз данных  
 **Server Explorer/Database Explorer** позволяет вам создавать подключения времени разработки к источникам данных. Это дает вам возможность просматривать доступные источники данных, отображать информацию о таблицах, столбцах и других содержащихся в них элементах, а также изменять и создавать элементы базы данных.  
  
 Приложение напрямую не используют подключения, доступные в **Server Explorer/Database Explorer**. Это подключения используются [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] для работы с базой данных во время разработки. Дополнительные сведения см. в разделе [Visual Database Tools](http://msdn.microsoft.com/en-us/6b145922-2f00-47db-befc-bf351b4809a1).  
  
 Например, во время разработки можно использовать **Server Explorer/Database Explorer** для создания подключения к базе данных. Позже, при разработке формы, можно просмотреть базу данных, выбрать столбцы из таблицы и перетащить их на [конструктор наборов данных](../data-tools/creating-and-editing-typed-datasets.md). При этом создается [TableAdapter](../data-tools/tableadapter-overview.md) в наборе данных. Также создается новый объект подключения, являющийся частью нового адаптера таблицы.  
  
 Информация о подключениях времени разработки хранится на локальном компьютере независимо от конкретного проекта или решения. Таким образом, после установления подключения времени разработки во время работы в приложении появится в **Server Explorer/Database Explorer** каждый раз, когда вы работаете в [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], при условии, что и сервер, к которому подключение доступна точек. Дополнительные сведения см. в разделе [как: соединение с базой данных с помощью обозревателя сервера](http://msdn.microsoft.com/en-us/7c1c3067-0d77-471b-872b-639f9f50db74).  
  
 [!INCLUDE[SQLObjectExplorer](../includes/sqlobjectexplorer-md.md)]  
  
## <a name="see-also"></a>См. также  
 [Подключение к данным в Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Практическое руководство. Подключение к данным в базе данных](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Пошаговое руководство: Подключение к данным в базе данных (Windows Forms)](http://msdn.microsoft.com/library/02d39aa6-8993-4602-be13-a13536af3d1c)   
 [Схема содержимого для доступа к данным ASP.NET](http://msdn.microsoft.com/en-us/f9219396-a0fa-481f-894d-e3d9c67d64f2)   
 [Подготовка приложения для получения данных](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Выборка данных в приложение](../data-tools/fetching-data-into-your-application.md)   
 [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Редактирование данных в приложении](../data-tools/editing-data-in-your-application.md)   
 [Проверка данных](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Сохранение данных](../data-tools/saving-data.md)
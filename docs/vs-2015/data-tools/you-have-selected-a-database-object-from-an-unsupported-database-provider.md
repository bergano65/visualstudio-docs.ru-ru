---
title: Выбран объект базы данных от поставщика базы данных не поддерживается | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2c225e00a6d303bff16e30fabd2f3e8e0e9d40ca
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47571545"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Выбран объект базы данных из неподдерживаемого поставщика базы данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [документация по Visual Studio 2017](https://docs.microsoft.com/en-us/visualstudio/).  
  
[!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) Поддерживает только поставщик данных .NET Framework для SQL Server (<xref:System.Data.SqlClient>). Несмотря на то, что можно щелкнуть **ОК** и продолжить работу с объектами из неподдерживаемых поставщиков базы данных, можно испытать неожиданное поведение во время выполнения.  
  
> [!NOTE]
>  Поддерживаются только данные о соединениях, которые используют .NET Framework Data Provider for SQL Server.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Нажмите кнопку **ОК** продолжить построение классов сущностей, которые сопоставляются соединение, которое использует неподдерживаемый поставщик базы данных. Можно испытать неожиданное поведение, когда используете неподдерживаемых поставщиков базы данных.  
  
     - или -  
  
-   Нажмите кнопку **отменить**.  
  
     Действие отменяется. Создайте или используйте данные о подключении, которое использует .NET Framework Provider for SQL Server.  
  
## <a name="see-also"></a>См. также  
 [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Поставщики данных .NET framework](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131)   
 [Подключение к данным в Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)


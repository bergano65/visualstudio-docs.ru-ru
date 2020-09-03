---
title: Выбранное соединение использует неподдерживаемый поставщик базы данных | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 4d25dfa1-8fa4-4529-9b90-973bc2ec2993
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4e79d8408fba54cf192d51f9d2ead8c0ffafe1f0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667196"
---
# <a name="the-selected-connection-uses-an-unsupported-database-provider"></a>Выбранное подключение использует неподдерживаемый поставщик базы данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Это сообщение появляется при перетаскивании элементов, не использующих .NET Framework поставщика данных для SQL Server из **Обозреватель сервера** / **Обозреватель базы данных** [в средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md).

 [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] поддерживает только данные о соединениях, которые используют .NET Framework Provider для SQL Server. Допустимы только подключения к Microsoft SQL Server или Microsoft SQL Server Database File.

### <a name="to-correct-this-error"></a>Исправление ошибки

- В [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] из данных о соединениях добавляйте только элементы, которые используют .NET Framework Data Provider for SQL Server.

## <a name="see-also"></a>См. также:
 <xref:System.Data.SqlClient>Пошаговое руководство по [.NET Framework поставщиков данных](https://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131) [: создание классов LINQ to SQL (реляционный конструктор R)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)
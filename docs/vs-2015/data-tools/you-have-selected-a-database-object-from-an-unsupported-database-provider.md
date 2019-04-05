---
title: Выбран объект базы данных от поставщика базы данных не поддерживается | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4021d6413acbe895995ee25809deb250daf6872c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58980323"
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Выбран объект базы данных из неподдерживаемого поставщика базы данных
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) Поддерживает только поставщик данных .NET Framework для SQL Server (<xref:System.Data.SqlClient>). Хотя можно нажать кнопку **OK** и продолжить работу с объектами из неподдерживаемых поставщиков базы данных, можно испытать неожиданное поведение во время выполнения.  
  
> [!NOTE]
>  Поддерживаются только данные о соединениях, которые используют .NET Framework Data Provider for SQL Server.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
-   Нажмите кнопку **OK**, чтобы продолжить построение классов сущностей, сопоставляемым подключению, которое использует неподдерживаемые поставщики базы данных. Можно испытать неожиданное поведение, когда используете неподдерживаемых поставщиков базы данных.  
  
     - или -  
  
-   Нажмите кнопку **Отмена**.  
  
     Действие отменяется. Создайте или используйте данные о подключении, которое использует .NET Framework Provider for SQL Server.  
  
## <a name="see-also"></a>См. также  
 [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Поставщики данных .NET Framework](http://msdn.microsoft.com/library/03a9fc62-2d24-491a-9fe6-d6bdb6dcb131)   
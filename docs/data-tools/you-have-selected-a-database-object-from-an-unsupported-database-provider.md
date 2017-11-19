---
title: "Выбран объект базы данных из неподдерживаемых поставщиков базы данных | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0f1298e-31aa-471e-ae19-1bafffd2ae40
caps.latest.revision: "3"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 05e638be5cc11f66052e5a1f6116e7205b824106
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/09/2017
---
# <a name="you-have-selected-a-database-object-from-an-unsupported-database-provider"></a>Выбран объект базы данных из неподдерживаемого поставщика базы данных
Реляционный конструктор объектов поддерживает только поставщик данных .NET Framework для SQL Server (<xref:System.Data.SqlClient>). Несмотря на то, что можно щелкнуть **ОК** и продолжить работу с объектами из неподдерживаемых поставщиков базы данных, можно испытать неожиданное поведение во время выполнения.  
  
> [!NOTE]
>  Поддерживаются только данные о соединениях, которые используют .NET Framework Data Provider for SQL Server.  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
- Нажмите кнопку **ОК**.

   Вы можете продолжить построение классов сущностей, сопоставляемым подключению, которое использует неподдерживаемых поставщиков базы данных. Можно испытать неожиданное поведение, когда используете неподдерживаемых поставщиков базы данных.  
  
     -или-  
  
- Нажмите кнопку **отменить**.

   Действие отменяется. Создайте или используйте данные о подключении, которое использует .NET Framework Provider for SQL Server.  
  
## <a name="see-also"></a>См. также
[Сообщения реляционного конструктора объектов](../data-tools/o-r-designer-messages.md)  
[Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
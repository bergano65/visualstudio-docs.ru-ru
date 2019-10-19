---
title: Практическое руководство. Сохранение данных с помощью транзакции
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: cfb03944743609d20d14f6104e5fadd529a5cfa6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72641311"
---
# <a name="how-to-save-data-by-using-a-transaction"></a>Практическое руководство. Сохранение данных с помощью транзакции

Данные сохраняются в транзакции с помощью пространства имен <xref:System.Transactions>. Используйте объект <xref:System.Transactions.TransactionScope> для участия в транзакции, которая автоматически управляется.

Проекты не создаются со ссылкой на сборку *System. Transactions* , поэтому необходимо вручную добавить ссылку на проекты, использующие транзакции.

Самым простым способом реализации транзакции является создание экземпляра объекта <xref:System.Transactions.TransactionScope> в инструкции `using`. (Дополнительные сведения см. в разделе [оператор using](/dotnet/visual-basic/language-reference/statements/using-statement)и [оператор using](/dotnet/csharp/language-reference/keywords/using-statement).) Код, который выполняется в инструкции `using`, участвует в транзакции.

Чтобы зафиксировать транзакцию, вызовите метод <xref:System.Transactions.TransactionScope.Complete%2A> в качестве последней инструкции в блоке using.

Чтобы выполнить откат транзакции, вызовите исключение перед вызовом метода <xref:System.Transactions.TransactionScope.Complete%2A>.

## <a name="to-add-a-reference-to-the-systemtransactionsdll"></a>Добавление ссылки на библиотеку System. Transactions. dll

1. В меню **проект** выберите команду **Добавить ссылку**.

2. На вкладке **.NET** (вкладка "**SQL Server** " для SQL Server проектов) выберите **System. Transactions**и нажмите кнопку **ОК**.

     В проект добавляется ссылка на *библиотеку System. Transactions. dll* .

## <a name="to-save-data-in-a-transaction"></a>Сохранение данных в транзакции

- Добавьте код для сохранения данных в инструкции using, содержащей транзакцию. В следующем коде показано, как создать объект <xref:System.Transactions.TransactionScope> и создать его экземпляр в операторе using:

     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]

## <a name="see-also"></a>См. также

- [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)
- [Пошаговое руководство. Сохранение данных в транзакции](../data-tools/save-data-in-a-transaction.md)
---
title: Сохранение данных с помощью транзакции | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- saving data, using transactions
- System.Transactions namespace
- transactions, saving data
- data [Visual Studio], saving
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 85f3584073523e748168faf569aa918ba912fbf8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652835"
---
# <a name="save-data-by-using-a-transaction"></a>Сохранение данных с помощью транзакции
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Данные сохраняются в транзакции с помощью пространства имен <xref:System.Transactions>. Используйте объект <xref:System.Transactions.TransactionScope> для участия в транзакции, которая автоматически управляется.

 Проекты не создаются со ссылкой на сборку System. Transactions, поэтому необходимо вручную добавить ссылку на проекты, использующие транзакции.

> [!NOTE]
> Пространство имен <xref:System.Transactions> поддерживается в Windows 2000 или более поздней версии.

 Самым простым способом реализации транзакции является создание экземпляра объекта <xref:System.Transactions.TransactionScope> в инструкции `using`. (Дополнительные сведения см. в разделе [оператор using](https://msdn.microsoft.com/library/665d1580-dd54-4e96-a9a9-6be2a68948f1)и [оператор using](https://msdn.microsoft.com/library/afc355e6-f0b9-4240-94dd-0d93f17d9fc3).) Код, который выполняется в инструкции `using`, участвует в транзакции.

 Чтобы зафиксировать транзакцию, вызовите метод <xref:System.Transactions.TransactionScope.Complete%2A> в качестве последней инструкции в блоке using.

 Чтобы выполнить откат транзакции, вызовите исключение перед вызовом метода <xref:System.Transactions.TransactionScope.Complete%2A>.

 Дополнительные сведения см. [в разделе Сохранение данных в транзакции](../data-tools/save-data-in-a-transaction.md).

### <a name="to-add-a-reference-to-the-systemtransactions-dll"></a>Добавление ссылки на библиотеку DLL System. Transactions

1. В меню **проект** выберите команду **Добавить ссылку**.

2. На вкладке **.NET** (вкладка "**SQL Server** " для SQL Server проектов) выберите **System. Transactions**и нажмите кнопку **ОК**.

     В проект добавляется ссылка на библиотеку System. Transactions. dll.

### <a name="to-save-data-in-a-transaction"></a>Сохранение данных в транзакции

- Добавьте код для сохранения данных в инструкции using, содержащей транзакцию. В следующем коде показано, как создать объект <xref:System.Transactions.TransactionScope> и создать его экземпляр в операторе using:

     [!code-csharp[VbRaddataSaving#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#11)]
     [!code-vb[VbRaddataSaving#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#11)]

## <a name="see-also"></a>См. также раздел
 [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)

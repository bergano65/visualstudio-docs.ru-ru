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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c133bb3f8ef56378c20b985aa118e48e71109cea
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60065263"
---
# <a name="save-data-by-using-a-transaction"></a>Сохранение данных с помощью транзакции
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Сохранение данных в транзакции с помощью <xref:System.Transactions> пространства имен. Используйте <xref:System.Transactions.TransactionScope> объекту участвовать в транзакции, которая автоматически осуществляется автоматически.  
  
 Проекты не создаются со ссылкой на сборку System.Transactions, поэтому вам нужно вручную добавить ссылку на проекты, использующие транзакции.  
  
> [!NOTE]
>  <xref:System.Transactions> Пространство имен поддерживается в Windows 2000 или более поздней версии.  
  
 Самый простой способ реализации транзакции является создание экземпляра <xref:System.Transactions.TransactionScope> объекта в `using` инструкции. (Дополнительные сведения см. в разделе [Оператор Using](http://msdn.microsoft.com/library/665d1580-dd54-4e96-a9a9-6be2a68948f1), и [инструкцией](http://msdn.microsoft.com/library/afc355e6-f0b9-4240-94dd-0d93f17d9fc3).) Код, выполняемый в рамках `using` инструкции участвует в транзакции.  
  
 Чтобы зафиксировать транзакцию, вызвать <xref:System.Transactions.TransactionScope.Complete%2A> метод в последнем операторе в с помощью блокируется.  
  
 Чтобы откатить транзакцию, исключение до вызова метода <xref:System.Transactions.TransactionScope.Complete%2A> метод.  
  
 Дополнительные сведения см. в разделе [сохранение данных в транзакции](../data-tools/save-data-in-a-transaction.md).  
  
### <a name="to-add-a-reference-to-the-systemtransactions-dll"></a>Чтобы добавить ссылку на библиотеку DLL System.Transactions  
  
1. На **проекта** меню, выберите **добавить ссылку**.  
  
2. На **.NET** вкладке (**SQL Server** вкладку для проектов SQL Server), выберите **System.Transactions**, а затем выберите **ОК**.  
  
     В проект добавляется ссылка на файл System.Transactions.dll.  
  
### <a name="to-save-data-in-a-transaction"></a>Чтобы сохранить данные в транзакции  
  
- Добавьте код для сохранения данных с помощью инструкции, содержащей транзакции. Ниже показано, как создать и создание экземпляра <xref:System.Transactions.TransactionScope> объекта в с помощью инструкции:  
  
     [!code-csharp[VbRaddataSaving#11](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#11)]
     [!code-vb[VbRaddataSaving#11](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#11)]  
  
## <a name="see-also"></a>См. также  
 [Сохранение данных обратно в базу данных](../data-tools/save-data-back-to-the-database.md)

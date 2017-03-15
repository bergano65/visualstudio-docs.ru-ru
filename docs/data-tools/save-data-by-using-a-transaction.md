---
title: "Практическое руководство. Сохранение данных с помощью транзакции | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "данные [Visual Studio], сохранение"
  - "сохранение данных, использование транзакций"
  - "System.Transactions - пространство имен"
  - "транзакции, сохранение данных"
ms.assetid: 8b835e8f-34a3-413d-9bb5-ebaeb87f1198
caps.latest.revision: 13
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Практическое руководство. Сохранение данных с помощью транзакции
Данные сохраняются в транзакции с использованием пространства имен <xref:System.Transactions>.  Используйте объект <xref:System.Transactions.TransactionScope> для выполнения автоматически управляемой транзакции.  
  
 Проекты не создаются со ссылкой на сборку System.Transactions, поэтому требуется вручную добавить ссылку на проекты, использующие транзакции.  
  
> [!NOTE]
>  Пространство имен <xref:System.Transactions> поддерживается в Windows 2000 и более поздних версиях Windows.  
  
 Самый простой способ реализации транзакции — это создание экземпляра объекта <xref:System.Transactions.TransactionScope> в инструкции `using`.  \(Дополнительные сведения см. в разделе [Оператор Using](/dotnet/visual-basic/language-reference/statements/using-statement) и [Оператор using](/dotnet/csharp/language-reference/keywords/using-statement).\) Код, выполняемый в инструкции `using`, будет участвовать в транзакции.  
  
 Чтобы зафиксировать транзакцию, вызовите метод <xref:System.Transactions.TransactionScope.Complete%2A> в качестве последней инструкции в блоке using.  
  
 Для отката транзакции вызовите исключение до вызова метода <xref:System.Transactions.TransactionScope.Complete%2A>.  
  
 Дополнительные сведения см. в разделе [Пошаговое руководство. Сохранение данных в транзакции](../data-tools/save-data-in-a-transaction.md).  
  
### Чтобы добавить ссылку на библиотеку DLL System.Transactions  
  
1.  В меню **Проект** выберите **Добавить ссылку**.  
  
2.  Выберите **System.Transactions** на вкладке **.NET** \(на вкладке **SQL Server** для проектов SQL Server\) и нажмите кнопку **OK**.  
  
     Ссылка на библиотеку System.Transactions.dll будет добавлена в проект.  
  
### Чтобы сохранить данные в транзакции  
  
-   Добавьте код для сохранения данных внутри оператора using, содержащего транзакцию.  В следующем коде демонстрируется создание экземпляра объекта <xref:System.Transactions.TransactionScope> в операторе using:  
  
     [!code-vb[VbRaddataSaving#11](../data-tools/codesnippet/VisualBasic/save-data-by-using-a-transaction_1.vb)]
     [!code-cs[VbRaddataSaving#11](../data-tools/codesnippet/CSharp/save-data-by-using-a-transaction_1.cs)]  
  
## См. также  
 [Пошаговое руководство. Сохранение данных в транзакции](../data-tools/save-data-in-a-transaction.md)   
 [Привязка элементов управления Windows Forms к данным в Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Общие сведения о приложениях для работы с данными в Visual Studio](../data-tools/overview-of-data-applications-in-visual-studio.md)   
 [Подключение к данным в Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Подготовка приложения к получению данных](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Выборка данных в приложение](../data-tools/fetching-data-into-your-application.md)   
 [Привязка элементов управления к данным в Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Редактирование данных в приложении](../data-tools/editing-data-in-your-application.md)   
 [Проверка данных](../Topic/Validating%20Data.md)   
 [Сохранение данных](../data-tools/saving-data.md)
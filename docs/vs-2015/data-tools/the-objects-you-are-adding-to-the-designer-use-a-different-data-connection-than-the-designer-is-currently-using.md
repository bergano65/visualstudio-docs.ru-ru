---
title: При добавлении в конструктор объекты используют другое подключение к данным, чем в настоящее время с помощью конструктора | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 773d3ea2e0d5574b194a44783b14d35db25d6f7f
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/17/2019
ms.locfileid: "59661832"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer-is-currently-using"></a>Добавляемые в конструктор объекты используют подключение данных, отличное от текущего подключения конструктора
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Подключение к данным, используемое для добавляемого в конструктор объекта, отличается от подключения, используемого конструктором в настоящий момент. Вы хотите заменить подключение, используемое конструктором?  
  
 При добавлении элементов к [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]), все элементы используют общее подключение к данным. (Область конструктора предоставляет <xref:System.Data.Linq.DataContext>, которое использует единое подключение к данным для всех объектов на области конструктора). Если к конструктору добавляется объект, который использует подключение к данным, которое отличается от подключения к данным, в настоящее время используемого конструктором, появляется это сообщение. Для устранения этой ошибки можно выбрать поддержку существующего подключения. Если вы делаете это выбор, то выбранный объект не будет добавлен. В противном случае можно выбрать добавление объекта и переустановить соединение <xref:System.Data.Linq.DataContext> на новое соединение.  
  
> [!NOTE]
>  Если щелкнуть **Да**, все классы сущностей в [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] сопоставляются с новым соединением.  
  
### <a name="to-replace-the-existing-connection-with-the-connection-used-by-the-selected-object"></a>Для замены существующего подключения соединением, используемым выбранным объектом  
  
-   Нажмите кнопку **Да**.  
  
     Выбранный объект добавляется к [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], и подключение DataContext.Connection устанавливается на новое подключение.  
  
### <a name="to-continue-to-use-the-existing-connection-and-cancel-adding-the-selected-object"></a>Чтобы продолжить использование существующего подключения и отказаться от добавления выбранного объекта  
  
-   Нажмите кнопку **Нет**.  
  
     Действие отменяется. DataContext.Connection остается установленным на существующее подключение.  
  
## <a name="see-also"></a>См. также  
 [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
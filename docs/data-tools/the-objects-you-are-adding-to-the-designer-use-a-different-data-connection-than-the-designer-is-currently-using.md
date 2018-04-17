---
title: Объекты добавляются в конструктор, используют другое подключение к данным, чем в настоящее время с помощью конструктора | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c738a9beb0f2807a186a7c8b8e3f7138c82c9bfa
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer-is-currently-using"></a>Добавляемые в конструктор объекты используют подключение данных, отличное от текущего подключения конструктора
Подключение к данным, используемое для добавляемого в конструктор объекта, отличается от подключения, используемого конструктором в настоящий момент. Вы хотите заменить подключение, используемое конструктором?  
  
 При добавлении элементов к [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] ([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]), все элементы используют общее подключение к данным. (Область конструктора предоставляет <xref:System.Data.Linq.DataContext>, которое использует единое подключение к данным для всех объектов на области конструктора). Если к конструктору добавляется объект, который использует подключение к данным, которое отличается от подключения к данным, в настоящее время используемого конструктором, появляется это сообщение. Для устранения этой ошибки можно выбрать поддержку существующего подключения. Если вы делаете это выбор, то выбранный объект не будет добавлен. Кроме того, вы можете добавить объект и сбросить <xref:System.Data.Linq.DataContext> соединение с новым соединением.  
  
> [!NOTE]
>  Если щелкнуть **Да**, все классы сущностей [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] сопоставляются с новым соединением.  
  
### <a name="to-replace-the-existing-connection-with-the-connection-used-by-the-selected-object"></a>Для замены существующего подключения соединением, используемым выбранным объектом  
  
-   Нажмите кнопку **Да**.  
  
     Выбранный объект добавляется к [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], и подключение DataContext.Connection устанавливается на новое подключение.  
  
### <a name="to-continue-to-use-the-existing-connection-and-cancel-adding-the-selected-object"></a>Чтобы продолжить использование существующего подключения и отказаться от добавления выбранного объекта  
  
-   Нажмите кнопку **Нет**.  
  
     Действие отменяется. DataContext.Connection остается установленным на существующее подключение.  
  
## <a name="see-also"></a>См. также
[Сообщения реляционного конструктора объектов](../data-tools/o-r-designer-messages.md)  
[Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
 
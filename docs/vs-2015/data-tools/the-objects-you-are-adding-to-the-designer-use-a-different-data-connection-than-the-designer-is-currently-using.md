---
title: Объекты, добавляемые в конструктор, используют другое подключение к данным, отличное от используемого конструктором | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 332ed2f3-3377-4d51-8e3b-fdb98231978e
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d9ec76446aff930475ea5e3ca0133e11b3798b0c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672292"
---
# <a name="the-objects-you-are-adding-to-the-designer-use-a-different-data-connection-than-the-designer-is-currently-using"></a>Добавляемые в конструктор объекты используют подключение данных, отличное от текущего подключения конструктора
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Подключение к данным, используемое для добавляемого в конструктор объекта, отличается от подключения, используемого конструктором в настоящий момент. Вы хотите заменить подключение, используемое конструктором?

 При добавлении элементов в [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)] ([!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]) все элементы используют одно общее подключение к данным. (Область конструктора представляет <xref:System.Data.Linq.DataContext>, которая использует одно соединение для всех объектов на поверхности.) Если добавить в конструктор объект, использующий подключение к данным, которое отличается от подключения к данным, используемым в данный момент конструктором, отображается это сообщение. Для устранения этой ошибки можно выбрать поддержку существующего подключения. Если вы делаете это выбор, то выбранный объект не будет добавлен. В противном случае можно выбрать добавление объекта и переустановить соединение <xref:System.Data.Linq.DataContext> на новое соединение.

> [!NOTE]
> Если нажать кнопку **Да**, все классы сущностей в [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] сопоставлены с новым соединением.

### <a name="to-replace-the-existing-connection-with-the-connection-used-by-the-selected-object"></a>Для замены существующего подключения соединением, используемым выбранным объектом

- Щелкните **Да**.

     Выбранный объект добавляется к [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], и подключение DataContext.Connection устанавливается на новое подключение.

### <a name="to-continue-to-use-the-existing-connection-and-cancel-adding-the-selected-object"></a>Чтобы продолжить использование существующего подключения и отказаться от добавления выбранного объекта

- Нажмите кнопку **Нет**.

     Действие отменяется. DataContext.Connection остается установленным на существующее подключение.

## <a name="see-also"></a>См. также раздел
 [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
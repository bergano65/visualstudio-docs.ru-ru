---
title: Один или несколько выбранных элементов содержат тип данных, который не поддерживается конструктором | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 966adc7a4114c54479c0ad8c52a604e0fb5d3380
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Один или несколько выбранных элементов содержат тип данных, не поддерживаемый конструктором
Один или несколько элементов перетащить из **обозревателя серверов**/**обозреватель баз данных** на [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] содержит тип данных, который не поддерживается [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] например, [Определяемых пользователем типов CLR](/dotnet/framework/data/adonet/sql/clr-user-defined-types).  
  
### <a name="to-correct-this-error"></a>Исправление ошибки  
  
1.  Создайте представление, которое основано на нужной таблице и которое не включает неподдерживаемый тип данных.  
  
2.  Перетащите представление из **обозревателя серверов**/**обозреватель баз данных** в конструктор.  
  
## <a name="see-also"></a>См. также
[Сообщения реляционного конструктора объектов](../data-tools/o-r-designer-messages.md)  
[Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
---
title: 'Как: расширение кода, созданного в конструкторе O R | Документы Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 7d1c8df8dfeb6f6aec7acaf0545f348e81b97192
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>Практическое руководство. Расширение кода, созданного реляционным конструктором объектов
Код, сгенерированный конструктором [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], генерируется заново, когда выполняются изменения в классах сущностей и в других объектах на области конструктора. Из-за этой повторной генерации кода, любой код, который добавляется к сгенерированному коду, обычно перезаписывается, когда конструктор заново генерирует код. Конструктор [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] обеспечивает способность генерировать файлы разделяемых классов, в которые можно добавлять код, который не будет перезаписываться. Один пример добавления собственного кода к коду, сгенерированному конструктором [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] состоит в добавлении проверки данных в классы сущностей LINQ to SQL. Сведения см. в разделе [как: Добавление проверки в классы сущностей](../data-tools/how-to-add-validation-to-entity-classes.md).  
  
[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## <a name="adding-code-to-an-entity-class"></a>Добавление кода в класс сущностей  
  
#### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>Для создания разделяемого класса и добавления кода в класс сущностей  
  
1.  Откройте или создайте новый файл классов LINQ to SQL Classes (**.dbml** файл) в [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. (Дважды щелкните **.dbml** файла в **обозревателе решений**/**обозревателя базы данных**.)  
  
2.  В [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], щелкните правой кнопкой мыши класс, для которого вы хотите добавить проверку, а затем нажмите кнопку **Просмотр кода**.  
  
     Открывается Редактор кода с разделяемым классом для выбранного класса сущностей.  
  
3.  Добавьте код объявление разделяемого класса для класса сущностей.  
  
## <a name="adding-code-to-a-datacontext"></a>Добавление кода в DataContext  
  
#### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>Для создания разделяемого класса и добавления кода в DataContext  
  
1.  Откройте или создайте новый файл классов LINQ to SQL Classes (**.dbml** файл) в [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]. (Дважды щелкните **.dbml** файла в **обозревателе решений**/**обозревателя базы данных**.)  
  
2.  В [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], щелкните правой кнопкой мыши пустую область конструктора, а затем нажмите кнопку **Просмотр кода**.  
  
     Открывается Редактор кода с разделяемым классом для DataContext.  
  
3.  Добавьте код в объявление разделяемого класса для DataContext.  
  
## <a name="see-also"></a>См. также  
 [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Пошаговое руководство: Создание классов LINQ to SQL (конструктор O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)   
 [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)   
 
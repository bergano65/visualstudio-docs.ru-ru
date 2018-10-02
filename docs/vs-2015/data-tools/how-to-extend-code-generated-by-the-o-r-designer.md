---
title: 'Практическое: расширение кода, созданного с помощью реляционного конструктора | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8fe770e52a1557d577ef2536177321deb04c0128
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47564202"
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>Практическое руководство. Расширение кода, созданного реляционным конструктором объектов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [как: расширить код, созданный с помощью реляционного конструктора](https://docs.microsoft.com/visualstudio/data-tools/how-to-extend-code-generated-by-the-o-r-designer).  
  
  
Код, сгенерированный конструктором [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], генерируется заново, когда выполняются изменения в классах сущностей и в других объектах на области конструктора. Из-за этой повторной генерации кода, любой код, который добавляется к сгенерированному коду, обычно перезаписывается, когда конструктор заново генерирует код. Конструктор [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] обеспечивает способность генерировать файлы разделяемых классов, в которые можно добавлять код, который не будет перезаписываться. Один пример добавления собственного кода к коду, сгенерированному конструктором [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] состоит в добавлении проверки данных в классы сущностей LINQ to SQL. Сведения см. в разделе [как: Добавление проверки в классы сущностей](../data-tools/how-to-add-validation-to-entity-classes.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="adding-code-to-an-entity-class"></a>Добавление кода в класс сущностей  
  
#### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>Для создания разделяемого класса и добавления кода в класс сущностей  
  
1.  Откройте или создайте новый файл LINQ to SQL Classes (**.dbml** файл) в [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Дважды щелкните **.dbml** файл **обозревателе решений**/**обозреватель баз данных**.)  
  
2.  В [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], щелкните правой кнопкой мыши класс, для которого вы хотите добавить проверку, а затем нажмите кнопку **Просмотр кода**.  
  
     Открывается Редактор кода с разделяемым классом для выбранного класса сущностей.  
  
3.  Добавьте код объявление разделяемого класса для класса сущностей.  
  
## <a name="adding-code-to-a-datacontext"></a>Добавление кода в DataContext  
  
#### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>Для создания разделяемого класса и добавления кода в DataContext  
  
1.  Откройте или создайте новый файл LINQ to SQL Classes (**.dbml** файл) в [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Дважды щелкните **.dbml** файл **обозревателе решений**/**обозреватель баз данных**.)  
  
2.  В [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], щелкните правой кнопкой мыши пустую область в конструкторе и нажмите кнопку **Просмотр кода**.  
  
     Открывается Редактор кода с разделяемым классом для DataContext.  
  
3.  Добавьте код в объявление разделяемого класса для DataContext.  
  
## <a name="see-also"></a>См. также  
 [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [Пошаговое руководство: Создание классов LINQ to SQL (реляционный конструктор объектов)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Пошаговое руководство: Добавление проверки в классы сущностей](http://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)


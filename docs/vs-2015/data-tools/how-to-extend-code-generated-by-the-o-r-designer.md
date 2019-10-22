---
title: Пошаговое руководство. расширение кода, созданного с помощью конструктора O-R | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: d6d1122e-2f55-4607-8d8b-48c3c22600fb
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a1d60090ca16907e16bb58970d793124c5bb2dec
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665949"
---
# <a name="how-to-extend-code-generated-by-the-or-designer"></a>Практическое руководство. Расширение кода, созданного реляционным конструктором объектов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Код, сгенерированный конструктором [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], генерируется заново, когда выполняются изменения в классах сущностей и в других объектах на области конструктора. Из-за этой повторной генерации кода, любой код, который добавляется к сгенерированному коду, обычно перезаписывается, когда конструктор заново генерирует код. Конструктор [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] обеспечивает способность генерировать файлы разделяемых классов, в которые можно добавлять код, который не будет перезаписываться. Один пример добавления собственного кода к коду, сгенерированному конструктором [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] состоит в добавлении проверки данных в классы сущностей LINQ to SQL. Дополнительные сведения см. [в разделе как добавить проверку в классы сущностей](../data-tools/how-to-add-validation-to-entity-classes.md).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="adding-code-to-an-entity-class"></a>Добавление кода в класс сущностей

#### <a name="to-create-a-partial-class-and-add-code-to-an-entity-class"></a>Для создания разделяемого класса и добавления кода в класс сущностей

1. Откройте или создайте новый файл LINQ to SQL Classes (**DBML** -файл) в [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Дважды щелкните **DBML** -файл в **Обозреватель решений** /**Обозреватель базы данных**.)

2. В [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] щелкните правой кнопкой мыши класс, для которого требуется добавить проверку, и выберите пункт **Просмотреть код**.

     Открывается Редактор кода с разделяемым классом для выбранного класса сущностей.

3. Добавьте код объявление разделяемого класса для класса сущностей.

## <a name="adding-code-to-a-datacontext"></a>Добавление кода в DataContext

#### <a name="to-create-a-partial-class-and-add-code-to-a-datacontext"></a>Для создания разделяемого класса и добавления кода в DataContext

1. Откройте или создайте новый файл LINQ to SQL Classes (**DBML** -файл) в [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)]. (Дважды щелкните **DBML** -файл в **Обозреватель решений** /**Обозреватель базы данных**.)

2. В [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] щелкните правой кнопкой мыши пустую область в конструкторе и выберите пункт **Просмотреть код**.

     Открывается Редактор кода с разделяемым классом для DataContext.

3. Добавьте код в объявление разделяемого класса для DataContext.

## <a name="see-also"></a>См. также раздел
 Пошаговое руководство [по LINQ to SQL инструментов в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [. Создание классов LINQ to SQL (реляционный конструктор объектов)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [Пошаговое руководство. Добавление проверки в классы сущностей](https://msdn.microsoft.com/library/85b06a02-b2e3-4534-95b8-d077c8d4c1d7)

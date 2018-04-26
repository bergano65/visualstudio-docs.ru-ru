---
title: 'Как: Включение и выключение (конструктор O-R) плюрализации'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: a8c477ac276ce0ff9c292dc42ba2f5f7d1e53dd9
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Как: Включение и выключение (конструктор O/R) плюрализации
По умолчанию при перетаскивании объектов базы данных, имена которых заканчиваются на s или йства из **обозревателя серверов**/**обозреватель баз данных** на [средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), имена создаваемых классов сущностей изменяются с множественного числа на единственное. Это делается, чтобы более точно представить факт, что иллюстрируемый класс сущностей сопоставляется с единственной записью данных. Например, добавление таблицы Customers в [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] дает класс сущностей с именем Customer, поскольку класс будет содержать данные только для одного клиента.

> [!NOTE]
>  Преобразование во множественную форму включено по умолчанию только в версии Visual Studio для английского языка.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>Включение и отключение плюрализации

1.  В меню **Сервис** выберите пункт **Параметры**.

2.  В **параметры** диалогового окна разверните **инструменты для баз данных**.

    > [!NOTE]
    >  Выберите **Показать все параметры** Если **инструменты для баз данных** узла не отображается.

3.  Нажмите кнопку **реляционный конструктор объектов**.

4.  Задать **Плюрализация имен** для **включено** = **False** для задания [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] , чтобы имена классов не изменялись.

5.  Задать **Плюрализация имен** для **включено** = **True** Чтобы применить правила плюрализации к именам классов объектов, добавляемым [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].

## <a name="see-also"></a>См. также

- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Доступ к данным в Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
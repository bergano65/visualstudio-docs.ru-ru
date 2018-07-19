---
title: 'Практическое: Включение и отключение (реляционный конструктор объектов) плюрализации'
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
ms.openlocfilehash: 0a2d2e44efc284c38cfc450833839776effb9936
ms.sourcegitcommit: e9d1018a01af62c3dc5aeb6b325faba7e20bd496
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/28/2018
ms.locfileid: "37089387"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Практическое: Включение и отключение (реляционный конструктор объектов) плюрализации
По умолчанию, при перетаскивании объектов базы данных, имена которых заканчиваются на s или ies из **обозревателя серверов** или **обозреватель баз данных** на [средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), имена сгенерированных классов сущностей изменяются с множественного числа в единственном числе. Это делается, чтобы более точно представить факт, что иллюстрируемый класс сущностей сопоставляется с единственной записью данных. Например, добавление `Customers` таблицы **реляционный конструктор объектов** приводит класс сущностей с именем `Customer` так, как класс будет содержать данные для одного клиента.

> [!NOTE]
>  Преобразование во множественную форму включено по умолчанию только в версии Visual Studio для английского языка.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>Включение и отключение плюрализации

1.  В меню **Сервис** выберите пункт **Параметры**.

2.  В **параметры** диалоговом окне разверните **инструменты для баз данных**.

    > [!NOTE]
    >  Выберите **Показать все параметры** Если **инструменты для баз данных** узла не отображается.

3.  Нажмите кнопку **реляционный конструктор объектов**.

4.  Задайте **Плюрализация имен** для **включено** = **False** присвоить **реляционный конструктор объектов** таким образом, чтобы имена классов не изменялись .

5.  Задайте **Плюрализация имен** для **включено** = **True** Чтобы применить правила плюрализации к именам классов объектов, добавляемым **O/R Конструктор**.

## <a name="see-also"></a>См. также

- [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)
- [Доступ к данным в Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
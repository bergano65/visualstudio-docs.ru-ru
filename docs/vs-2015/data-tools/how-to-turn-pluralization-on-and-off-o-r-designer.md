---
title: Включение и отключение во множественном числе (реляционный конструктор R) | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: afe8c8a4429efb83c09d80a5dd00dfe08b0d63e3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665934"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Практическое руководство. Включение и выключение плюрализации (реляционный конструктор объектов)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

По умолчанию при перетаскивании объектов базы данных, имена которых оканчиваются на s или classes, из **обозреватель сервера** /**обозреватель базы данных** в [средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), имена созданных классов сущностей изменяются из множественного числа на ед. Это делается, чтобы более точно представить факт, что иллюстрируемый класс сущностей сопоставляется с единственной записью данных. Например, добавление таблицы Customers в [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] дает класс сущностей с именем Customer, поскольку класс будет содержать данные только для одного клиента.

> [!NOTE]
> Преобразование во множественную форму включено по умолчанию только в версии Visual Studio для английского языка.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-turn-pluralization-on-and-off"></a>Включение и отключение плюрализации

1. В меню **Сервис** выберите пункт **Параметры**.

2. В диалоговом окне **Параметры** разверните пункт **Инструменты базы данных**.

> [!NOTE]
> Выберите команду **Показать все настройки**, если узел **Средства базы данных** не виден.

1. Щелкните **Реляционный конструктор объектов**.

2. Задайте для параметра **Множественное преобразование имен** значение **Enabled**  = **false** , чтобы задать [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)], чтобы он не менял имена классов.

3. Задайте для **параметра множественное преобразование имен** значение **Enabled**  = **true** , чтобы правила множественного преобразования применялись к именам классов объектов, добавляемых в [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].

## <a name="see-also"></a>См. также раздел
 [Средства LINQ to SQL в Visual studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655) [доступ к данным в Visual Studio](../data-tools/accessing-data-in-visual-studio.md)

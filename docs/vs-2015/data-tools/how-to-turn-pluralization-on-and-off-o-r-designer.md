---
title: Практическое руководство. Включение и отключение (реляционный конструктор объектов) плюрализации | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9ff3f206f57a544053498def16318e0ed65b64ab
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58979182"
---
# <a name="how-to-turn-pluralization-on-and-off-or-designer"></a>Практическое руководство. Включение и отключение преобразования во множественную форму (реляционный конструктор объектов)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
По умолчанию, при перетаскивании объектов базы данных, имена которых заканчиваются на s или ies из **обозревателя серверов**/**обозреватель баз данных** на [средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md), имена сгенерированных классов сущностей изменяются с множественного числа на единственное. Это делается, чтобы более точно представить факт, что иллюстрируемый класс сущностей сопоставляется с единственной записью данных. Например, добавление таблицы Customers в [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] дает класс сущностей с именем Customer, поскольку класс будет содержать данные только для одного клиента.  
  
> [!NOTE]
>  Преобразование во множественную форму включено по умолчанию только в версии Visual Studio для английского языка.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-turn-pluralization-on-and-off"></a>Включение и отключение плюрализации  
  
1.  В меню **Сервис** выберите пункт **Параметры**.  
  
2.  В диалоговом окне **Параметры** разверните пункт **Инструменты базы данных**.  
  
> [!NOTE]
>  Выберите команду **Показать все настройки**, если узел **Средства базы данных** не виден.  
  
1.  Щелкните **Реляционный конструктор объектов**.  
  
2.  Задайте **Плюрализация имен** для **включено** = **False** присвоить [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] таким образом, чтобы имена классов не изменялись.  
  
3.  Задайте **Плюрализация имен** для **включено** = **True** Чтобы применить правила плюрализации к именам классов объектов, добавляемым [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)].  
  
## <a name="see-also"></a>См. также  
 [Средства LINQ to SQL в Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Доступ к данным в Visual Studio](../data-tools/accessing-data-in-visual-studio.md)

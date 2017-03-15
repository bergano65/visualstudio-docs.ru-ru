---
title: "Как отключить и включить преобразование во множественную форму (реляционный конструктор объектов) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Как отключить и включить преобразование во множественную форму (реляционный конструктор объектов)
По умолчанию, когда вы перетаскиваете объекты базы данных, которые могут иметь имена с окончаниями s или ies из **Обозревателя серверов**\/**Обозревателя базы данных** на [Реляционный конструктор объектов](../data-tools/linq-to-sql-tools-in-visual-studio2.md), имена сгенерированных классов сущностей изменяются с множественного числа на единственное.Это делается, чтобы более точно представить факт, что иллюстрируемый класс сущностей сопоставляется с единственной записью данных.Например, добавление таблицы Customers в [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] дает класс сущностей с именем Customer, поскольку класс будет содержать данные только для одного клиента.  
  
> [!NOTE]
>  Преобразование во множественную форму включено по умолчанию только в версии Visual Studio для английского языка.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### Включение и отключение плюрализации  
  
1.  В меню **Сервис** выберите пункт **Параметры**.  
  
2.  В диалоговом окне **Параметры** разверните пункт **Инструменты базы данных**.  
  
> [!NOTE]
>  Выберите команду **Показать все настройки**, если узел **Средства базы данных** не виден.  
  
1.  Щелкните **Конструктор O\/R**.  
  
2.  Задайте параметру **Плюрализация имен** в поле **Включено** \= **False**, чтобы установить [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] так, чтобы имена классов не изменялись.  
  
3.  Задайте параметру **Плюрализация имен** в поле **Enabled** \= **True**, чтобы применить правила плюрализации к именам классов объектов, добавляемым в [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
## См. также  
 [Реляционный конструктор объектов](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Доступ к данным в Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
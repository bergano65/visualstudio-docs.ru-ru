---
title: "Пошаговые руководства по настройке Visual Studio с помощью пакетов VSPackage | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPackage"
  - "учебники"
  - "настройка visual studio"
  - "интегрированная среда разработки Visual Studio"
  - "интегрированная среда разработки visual studio"
ms.assetid: 7d10e376-74de-4402-9c10-ee9c9aa33c98
caps.latest.revision: 17
caps.handback.revision: 17
manager: "douge"
---
# Пошаговые руководства по настройке Visual Studio с помощью пакетов VSPackage
Visual Studio можно расширять путем создания пакетов VSPackage. Это программные модули, из которых состоит сама среда Visual Studio. Окна инструментов, редакторы, службы и типы проектов — все это пакеты VSPackage. Пакет SDK для Visual Studio позволяет создавать собственные пакеты VSPackage.  
  
 С помощью пошаговых руководств, приведенных в этом разделе, вы научитесь создавать пакеты VSPackage, реализовывать их функциональные возможности, интегрировать их в Visual Studio и предоставлять другим пользователям. Дополнительные сведения о пакетах VSPackage и их возможностях см. в разделе [В Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md).  
  
## В этом подразделе  
 [Создание расширения с помощью команды меню](../extensibility/creating-an-extension-with-a-menu-command.md)  
 Показано, как создать пакет VSPackage, который добавляет команду в меню Visual Studio, и как добавить сочетание клавиш для вызова команды. Также показано, как добавить сведения о пакете в диалоговое окно **О программе** и на экран\-заставку в Visual Studio.  
  
 [Добавление окна инструментов](../extensibility/adding-a-tool-window.md)  
 Показано, как создать окно инструментов в Visual Studio, а затем внедрить в него элемент управления и добавить панель команд. Также показано, как зарегистрировать окно инструментов для размещения в Visual Studio.  
  
 [Расширение свойств, список задач, выходные данные и параметры Windows](../extensibility/extending-the-properties-task-list-output-and-options-windows.md)  
 Показано, как создать простейший диспетчер задач, который позволяет пользователям добавлять задачи в **список задач** и окно **выходных данных** Visual Studio . Добавленные задачи можно редактировать в окне **Свойства** Visual Studio. Также показано, как добавить страницу в диалоговое окно **Параметры**.  
  
## Связанные подразделы  
 [Введение в пакет SDK для Visual Studio](../Topic/Introducing%20the%20Visual%20Studio%20SDK.md)  
 Содержит обзор компонентов и средств, включенных в пакет SDK для Visual Studio, и описание их использования для расширения Visual Studio.  
  
 [В Visual Studio SDK](../extensibility/internals/inside-the-visual-studio-sdk.md)  
 Описывается настройка различных элементов интегрированной среды разработки Visual Studio.
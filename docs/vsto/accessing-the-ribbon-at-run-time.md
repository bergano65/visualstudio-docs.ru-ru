---
title: "Доступ к ленте во время выполнения | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Globals - класс, лента"
  - "лента [разработка решений Office в Visual Studio], доступ"
  - "RibbonManager - класс"
ms.assetid: 8a7c7c6d-1a18-4d6b-98ee-e483d41f0cd8
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Доступ к ленте во время выполнения
  Вы можете написать код, чтобы отобразить, скрыть или изменить ленту и позволить пользователям запускать код из элементов управления в настраиваемой области задач, панели действий или области формы Outlook.  
  
 Доступ к ленте осуществляется с помощью класса `Globals`.  Для проектов Outlook можно получить доступ к лентам, которые отображаются в конкретном окне инспектора или проводника Outlook.  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
## Доступ к ленте с помощью класса Globals  
 Вы можете использовать класс `Globals` для доступа к ленте в проекте уровня документа или проекте надстройки VSTO из любого места в проекте.  
  
 Дополнительные сведения о классе `Globals` см. в разделе [Глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
 Следующий пример использует класс `Globals` для доступа к пользовательской ленте с именем `Ribbon1` и задает текст `Hello World`, отображаемый в поле со списком на ленте.  
  
 [!code-csharp[Trin_Outlook_FR_Access#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/CS/ThisAddIn.cs#4)]
 [!code-vb[Trin_Outlook_FR_Access#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/VB/ThisAddIn.vb#4)]  
  
## Доступ к коллекции лент, которые отображаются в определенном окне инспектора Outlook  
 Вы можете получить доступ к коллекции лент, появляющихся в *инспекторах* Outlook.  Инспектор — это окно, которое открывается в Outlook при выполнении пользователем определенных задач, таких как создание электронного сообщения.  Для доступа к ленте окна инспектора вызовите свойство `Ribbons` класса `Globals` и передайте объект <xref:Microsoft.Office.Interop.Outlook.Inspector>, представляющий инспектор.  
  
 Следующий пример получает коллекцию лент в инспекторе, в котором фокус находится в данный момент.  Пример кода затем получает доступ к ленте `Ribbon1` и задает текст `Hello World`, отображаемый в поле со списком на ленте.  
  
 [!code-csharp[Trin_Outlook_FR_Access#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/CS/ThisAddIn.cs#5)]
 [!code-vb[Trin_Outlook_FR_Access#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/VB/ThisAddIn.vb#5)]  
  
## Доступ к коллекции лент, которые отображаются в определенном окне проводника Outlook  
 Вы можете получить доступ к коллекции лент, появляющихся в *проводнике* Outlook.  Проводник — это пользовательский интерфейс основного приложения экземпляра Outlook.  Для доступа к ленте окна проводника вызовите свойство `Ribbons` класса `Globals` и передайте объект <xref:Microsoft.Office.Interop.Outlook.Explorer>, представляющий проводник.  
  
 Следующий пример получает коллекцию лент проводника, в котором фокус находится в данный момент.  Пример кода затем получает доступ к ленте `Ribbon1` и задает текст `Hello World`, отображаемый в поле со списком на ленте.  
  
 [!code-csharp[Trin_Outlook_FR_Access#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/CS/ThisAddIn.cs#6)]
 [!code-vb[Trin_Outlook_FR_Access#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/VB/ThisAddIn.vb#6)]  
  
## См. также  
 [Обзор ленты](../vsto/ribbon-overview.md)   
 [Конструктор лент](../vsto/ribbon-designer.md)   
 [XML-ленты](../vsto/ribbon-xml.md)   
 [Общие сведения об объектной модели ленты](../vsto/ribbon-object-model-overview.md)   
 [Пошаговое руководство. Создание настраиваемой вкладки с помощью конструктора лент](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Пошаговое руководство. Обновление элементов управления на ленте во время выполнения](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Настройка ленты для Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Доступ к области формы во время выполнения](../vsto/accessing-a-form-region-at-run-time.md)  
  
  
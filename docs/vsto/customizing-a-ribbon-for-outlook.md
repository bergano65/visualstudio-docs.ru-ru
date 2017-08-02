---
title: "Настройка ленты для Outlook"
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
  - "настраиваемая лента, сведения о настройке ленты"
  - "настройка ленты, сведения о настройке ленты"
  - "инспекторы [разработка решений Office в Visual Studio]"
  - "Outlook [разработка решений Office в Visual Studio], лента"
  - "лента [разработка решений Office в Visual Studio], Outlook - приложение"
ms.assetid: 11d10e72-806d-4d5e-b080-139bd8633eaa
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# Настройка ленты для Outlook
  При настройке ленты в Microsoft Office Outlook необходимо знать, где в приложении отображается настраиваемая лента.  Outlook показывает ленту в пользовательском интерфейсе основного приложения и в окнах, открывающихся при выполнении пользователем определенных задач, таких как создание сообщений электронной почты.  Эти окна приложения называются инспекторами.  
  
 ![ссылка на видео](~/docs/data-tools/media/playvideo.gif "ссылка на видео") Для просмотра связанных демонстрационных видеороликов перейдите по ссылке [Как использовать конструктор ленты для настройки ленты в Outlook](http://go.microsoft.com/fwlink/?LinkID=130312).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Добавление настраиваемой ленты в пользовательский интерфейс основного приложения  
 Пользовательский интерфейс основного приложения в Outlook называется проводником.  Если вы используете элемент **Лента \(визуальный конструктор\)**, вы можете добавить ленту в проводник, щелкнув свойство **RibbonType** ленты в окне **Свойства** и выбрав **Microsoft.Outlook.Explorer**.  
  
## Назначение ленты инспектору  
 Вы можете указать инспектор, который требуется настроить, выбрав тип ленты, соответствующий классу сообщений для инспектора.  
  
 Если вы используете элемент **Лента \(визуальный конструктор\)**, щелкните свойство **RibbonType** ленты в окне **Свойства** и выберите один или несколько идентификаторов ленты из списка значений.  
  
 В проект можно добавить несколько лент.  Если несколько лент имеют одинаковый идентификатор, переопределите метод CreateRibbonExtensibilityObject в классе `ThisAddin` проекта, чтобы указать, какую ленту следует отображать во время выполнения.  Дополнительные сведения см. в разделе [Обзор ленты](../vsto/ribbon-overview.md).  Дополнительные сведения о каждом типе ленты см. в технической статье [Настройка ленты в Outlook 2007](http://msdn.microsoft.com/ru-ru/946e97ea-f556-4e84-8fac-01cd9214e170).  
  
## Указание типа ленты с помощью XML\-кода ленты  
 Если вы используете элемент **Лента \(XML\)**, проверьте значение параметра *ribbonID* в методе <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> и верните нужную ленту.  
  
 Метод <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> автоматически создается средой Visual Studio в файле кода ленты.  Параметр *ribbonID* представляет собой строку, определяющую проводник или тип инспектора.  Полный список возможных значений параметра *ribbonID* см. в технической статье [Настройка ленты в Outlook 2007](http://msdn.microsoft.com/ru-ru/946e97ea-f556-4e84-8fac-01cd9214e170).  
  
 В следующем примере кода показано, как показывать настраиваемую ленту только в инспекторе `Microsoft.Outlook.Mail.Compose`.  Этот инспектор открывается, когда пользователь создает сообщение электронной почты.  Отображаемая лента указывается в методе `GetResourceText()`, который создается в классе **Ribbon**.  Дополнительные сведения о классе **Ribbon** см. в разделе [XML-ленты](../vsto/ribbon-xml.md).  
  
 [!code-csharp[Trin_RibbonOutlookBasic#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_RibbonOutlookBasic/CS/Ribbon1.cs#1)]
 [!code-vb[Trin_RibbonOutlookBasic#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_RibbonOutlookBasic/VB/Ribbon1.vb#1)]  
  
## См. также  
 [Доступ к ленте во время выполнения](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Обзор ленты](../vsto/ribbon-overview.md)   
 [Конструктор лент](../vsto/ribbon-designer.md)   
 [XML-ленты](../vsto/ribbon-xml.md)  
  
  
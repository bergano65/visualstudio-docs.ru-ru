---
title: "Настройка ленты для Outlook | Документы Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Inspectors [Office development in Visual Studio]
- Outlook [Office development in Visual Studio], Ribbon
- customizing the Ribbon, about customizing the Ribbon
- custom Ribbon, about customizing the Ribbon
- Ribbon [Office development in Visual Studio], Outlook
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: 3a7ed84f9eea6c4301f0fe4882d63522df2975f3
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="customizing-a-ribbon-for-outlook"></a>Настройка ленты для Outlook
  При настройке ленты в Microsoft Office Outlook необходимо знать, где в приложении отображается настраиваемая лента. Outlook показывает ленту в пользовательском интерфейсе основного приложения и в окнах, открывающихся при выполнении пользователем определенных задач, таких как создание сообщений электронной почты. Эти окна приложения называются инспекторами.  
  
 ![ссылка на видео](../vsto/media/playvideo.gif "ссылку видео") связанные демонстрационные видеоролики см. в разделе [практические советы. Использование конструктора ленты для настройки ленты в Outlook?](http://go.microsoft.com/fwlink/?LinkID=130312).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## <a name="adding-a-custom-ribbon-to-the-main-application-ui"></a>Добавление настраиваемой ленты в пользовательский интерфейс основного приложения  
 Пользовательский интерфейс основного приложения в Outlook называется проводником. Если вы используете **Лента (визуальный конструктор)** элемента, можно добавить ленту в проводник, щелкнув **RibbonType** ленты в **свойства** окна а затем выбрав **Microsoft.Outlook.Explorer**.  
  
## <a name="assigning-a-ribbon-to-an-inspector"></a>Назначение ленты инспектору  
 Вы можете указать инспектор, который требуется настроить, выбрав тип ленты, соответствующий классу сообщений для инспектора.  
  
 Если вы используете **Лента (визуальный конструктор)** , щелкните **RibbonType** ленты в **свойства** окна, а затем выберите один или несколько ленте идентификаторы из список значений.  
  
 В проект можно добавить несколько лент. Если несколько лент имеют одинаковый идентификатор, переопределите метод CreateRibbonExtensibilityObject в `ThisAddin` класс объекта проекта, чтобы указать, какую ленту следует отображать во время выполнения. Дополнительные сведения см. в разделе [Обзор ленты](../vsto/ribbon-overview.md). Дополнительные сведения о каждом типе ленты см. в технической статье [Настройка ленты в Outlook 2007](http://msdn.microsoft.com/en-us/946e97ea-f556-4e84-8fac-01cd9214e170).  
  
## <a name="specifying-the-ribbon-type-by-using-ribbon-xml"></a>Указание типа ленты с помощью XML-кода ленты  
 Если вы используете **Лента (XML)** , проверьте значение *ribbonID* параметр в <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> метода и верните нужную ленту.  
  
 Метод <xref:Microsoft.Office.Core.IRibbonExtensibility.GetCustomUI%2A> автоматически создается средой Visual Studio в файле кода ленты. *RibbonID* параметр представляет собой строку, определяющую проводник или конкретный тип инспектора. Полный список возможных значений *ribbonID* параметра, см. в технической статье [Настройка ленты в Outlook 2007](http://msdn.microsoft.com/en-us/946e97ea-f556-4e84-8fac-01cd9214e170).  
  
 В следующем примере кода показано, как показывать настраиваемую ленту только в инспекторе `Microsoft.Outlook.Mail.Compose`. Этот инспектор открывается, когда пользователь создает сообщение электронной почты. Отображаемая лента указывается в `GetResourceText()` метод, который создается в **ленты** класса. Дополнительные сведения о **ленты** см. в описании [XML-ленты](../vsto/ribbon-xml.md).  
  
 [!code-csharp[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/CSharp/Trin_RibbonOutlookBasic/Ribbon1.cs#1)]
 [!code-vb[Trin_RibbonOutlookBasic#1](../vsto/codesnippet/VisualBasic/Trin_RibbonOutlookBasic/Ribbon1.vb#1)]  
  
## <a name="see-also"></a>См. также  
 [Accessing the Ribbon at Run Time](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Обзор ленты](../vsto/ribbon-overview.md)   
 [Конструктор лент](../vsto/ribbon-designer.md)   
 [XML-ленты](../vsto/ribbon-xml.md)  
  
  
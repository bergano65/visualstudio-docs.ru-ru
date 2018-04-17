---
title: Доступ к ленте во время выполнения | Документы Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Globals class, Ribbon
- Ribbon [Office development in Visual Studio], accessing
- RibbonManager class
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a6129779b66406ffe24dbe65e03b289cb917c1ae
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="accessing-the-ribbon-at-run-time"></a>Accessing the Ribbon at Run Time
  Вы можете написать код, чтобы отобразить, скрыть или изменить ленту и позволить пользователям запускать код из элементов управления в настраиваемой области задач, панели действий или области формы Outlook.  

 Доступ к ленте осуществляется с помощью класса `Globals`. Для проектов Outlook можно получить доступ к лентам, которые отображаются в конкретном окне инспектора или проводника Outlook.  

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  

## <a name="accessing-the-ribbon-by-using-the-globals-class"></a>Доступ к ленте с помощью класса Globals  
 Вы можете использовать класс `Globals` для доступа к ленте в проекте уровня документа или проекте надстройки VSTO из любого места в проекте.  

 Дополнительные сведения о `Globals` см. в описании [глобальный доступ к объектам в проектах Office](../vsto/global-access-to-objects-in-office-projects.md).  

 Следующий пример использует класс `Globals` для доступа к пользовательской ленте с именем `Ribbon1` и задает текст `Hello World`, отображаемый в поле со списком на ленте.  

 [!code-vb[Trin_Outlook_FR_Access#4](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#4)]
 [!code-csharp[Trin_Outlook_FR_Access#4](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#4)]  

## <a name="accessing-a-collection-of-ribbons-that-appear-in-a-specific-outlook-inspector-window"></a>Доступ к коллекции лент, которые отображаются в определенном окне инспектора Outlook  
 Можно получить доступ к коллекции лент, появляющихся в Outlook *инспекторов*. Инспектор — это окно, которое открывается в Outlook при выполнении пользователем определенных задач, таких как создание электронного сообщения. Для доступа к ленте окна инспектора вызовите свойство `Ribbons` класса `Globals` и передайте объект <xref:Microsoft.Office.Interop.Outlook.Inspector>, представляющий инспектор.  

 Следующий пример получает коллекцию лент в инспекторе, в котором фокус находится в данный момент. Пример кода затем получает доступ к ленте `Ribbon1` и задает текст `Hello World`, отображаемый в поле со списком на ленте.  

 [!code-vb[Trin_Outlook_FR_Access#5](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#5)]
 [!code-csharp[Trin_Outlook_FR_Access#5](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#5)]  

## <a name="accessing-a-collection-of-ribbons-that-appear-for-a-specific-outlook-explorer"></a>Доступ к коллекции лент, которые отображаются в определенном окне проводника Outlook  
 Можно получить доступ к коллекции лент, появляющихся в Outlook *Explorer*. Проводник — это пользовательский интерфейс основного приложения экземпляра Outlook. Для доступа к ленте окна проводника вызовите свойство `Ribbons` класса `Globals` и передайте объект <xref:Microsoft.Office.Interop.Outlook.Explorer>, представляющий проводник.  

 Следующий пример получает коллекцию лент проводника, в котором фокус находится в данный момент. Пример кода затем получает доступ к ленте `Ribbon1` и задает текст `Hello World`, отображаемый в поле со списком на ленте.  

 [!code-vb[Trin_Outlook_FR_Access#6](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#6)]
 [!code-csharp[Trin_Outlook_FR_Access#6](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#6)]  

## <a name="see-also"></a>См. также  
 [Обзор ленты](../vsto/ribbon-overview.md)   
 [Конструктор лент](../vsto/ribbon-designer.md)   
 [XML-ленты](../vsto/ribbon-xml.md)   
 [Общие сведения о модели объектов ленты](../vsto/ribbon-object-model-overview.md)   
 [Пошаговое руководство: Создание настраиваемой вкладки с помощью конструктора лент](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Пошаговое руководство: Обновление элементов управления на ленте во время выполнения](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)   
 [Настройка ленты для Outlook](../vsto/customizing-a-ribbon-for-outlook.md)   
 [Доступ к области формы во время выполнения](../vsto/accessing-a-form-region-at-run-time.md)  

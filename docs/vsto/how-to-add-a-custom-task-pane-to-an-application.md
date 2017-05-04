---
title: "Практическое руководство. Добавление настраиваемой панели задач в приложение | Microsoft Docs"
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
  - "настраиваемые области задач [разработка решений Office в Visual Studio], добавление к приложению"
  - "области задач [разработка решений Office в Visual Studio], добавление к приложению"
ms.assetid: 67b4ed5b-d77e-4630-b851-34bb25bdc9b3
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Практическое руководство. Добавление настраиваемой панели задач в приложение
  Вы можете добавить настраиваемую область задач в приложения, перечисленные выше, с помощью надстройки VSTO.  Дополнительные сведения см. в статье [Настраиваемые области задач](../vsto/custom-task-panes.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
> [!NOTE]  
>  Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях.  Это зависит от имеющегося выпуска Visual Studio и используемых параметров.  Дополнительные сведения см. в разделе [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ru-ru/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## Добавление настраиваемой панели задач в приложение  
  
#### Добавление настраиваемой панели задач в приложение  
  
1.  Откройте или создайте проект надстройки VSTO для одного из приложений, указанных выше.  Дополнительные сведения см. в статье [Практическое руководство. Создание проектов Office в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  В меню **Проект** выберите команду **Добавить пользовательский элемент управления**.  
  
3.  В диалоговом окне **Добавление нового элемента** измените имя нового пользовательского элемента управления на **MyUserControl**, а затем нажмите кнопку **Добавить**.  
  
     Пользовательский элемент управления откроется в конструкторе.  
  
4.  Добавьте один или несколько элементов управления Windows Forms из **панели элементов** в пользовательский элемент управления.  
  
5.  Откройте файл кода **ThisAddIn.cs** или **ThisAddIn.vb**.  
  
6.  Добавьте следующий код в класс `ThisAddIn`.  Этот код объявляет экземпляры `MyUserControl` и <xref:Microsoft.Office.Tools.CustomTaskPane> как члены класса `ThisAddIn`.  
  
     [!code-csharp[Trin_TaskPaneBasic#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneBasic/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_TaskPaneBasic#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneBasic/VB/ThisAddIn.vb#1)]  
  
7.  Добавьте следующий код в обработчик событий `ThisAddIn_Startup`.  Этот код создает новый объект <xref:Microsoft.Office.Tools.CustomTaskPane>, добавляя  объект `MyUserControl` в коллекцию `CustomTaskPanes`.  Код также отображает область задач.  
  
     [!code-csharp[Trin_TaskPaneBasic#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_TaskPaneBasic/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_TaskPaneBasic#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_TaskPaneBasic/VB/ThisAddIn.vb#2)]  
  
    > [!NOTE]  
    >  Этот код связывает настраиваемую область задач с активным окном приложения.  Для некоторых приложений может потребоваться изменить этот код, чтобы убедиться, что область задач отображается с другими документами или элементами в приложении.  Дополнительные сведения см. в разделе [Настраиваемые области задач](../vsto/custom-task-panes.md).  
  
## См. также  
 [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)   
 [Настраиваемые области задач](../vsto/custom-task-panes.md)   
 [Руководство. Автоматизация приложения в настраиваемой области задач](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)  
  
  
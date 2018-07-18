---
title: 'Как: добавление настраиваемой области задач в приложение'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- task panes [Office development in Visual Studio], adding to application
- custom task panes [Office development in Visual Studio], adding to application
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: b8608fcc263be4750c38b6fe3f84967f40dd34ab
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/25/2018
ms.locfileid: "34548818"
---
# <a name="how-to-add-a-custom-task-pane-to-an-application"></a>Как: добавление настраиваемой области задач в приложение
  Вы можете добавить настраиваемую область задач в приложения, перечисленные выше, с помощью надстройки VSTO. Дополнительные сведения см. в разделе [настраиваемых панелей задач](../vsto/custom-task-panes.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
> [!NOTE]  
>  Отображаемые на компьютере имена или расположения некоторых элементов пользовательского интерфейса Visual Studio могут отличаться от указанных в следующих инструкциях. Это зависит от имеющегося выпуска Visual Studio и используемых параметров. Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="add-a-custom-task-pane-to-an-application"></a>Добавление настраиваемой области задач в приложение  
  
### <a name="to-add-a-custom-task-pane-to-an-application"></a>Добавление настраиваемой панели задач в приложение  
  
1.  Откройте или создайте проект надстройки VSTO для одного из приложений, указанных выше. Дополнительные сведения см. в разделе [как: проектов Office, создайте в Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
2.  В меню **Проект** выберите команду **Добавить пользовательский элемент управления**.  
  
3.  В **Добавление нового элемента** диалогового окна измените имя нового пользовательского элемента управления для **MyUserControl**, а затем нажмите кнопку **добавить**.  
  
     Пользовательский элемент управления откроется в конструкторе.  
  
4.  Добавьте один или несколько элементов управления Windows Forms из **элементов** в пользовательский элемент управления.  
  
5.  Откройте **ThisAddIn.cs** или **ThisAddIn.vb** файл кода.  
  
6.  Добавьте следующий код в класс `ThisAddIn` . Этот код объявляет экземпляры `MyUserControl` и <xref:Microsoft.Office.Tools.CustomTaskPane> как члены класса `ThisAddIn` .  
  
     [!code-vb[Trin_TaskPaneBasic#1](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#1)]
     [!code-csharp[Trin_TaskPaneBasic#1](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#1)]  
  
7.  Добавьте следующий код в обработчик событий `ThisAddIn_Startup`. Этот код создает новый объект <xref:Microsoft.Office.Tools.CustomTaskPane>, добавляя  объект `MyUserControl` в коллекцию `CustomTaskPanes`. Код также отображает область задач.  
  
     [!code-vb[Trin_TaskPaneBasic#2](../vsto/codesnippet/VisualBasic/Trin_TaskPaneBasic/ThisAddIn.vb#2)]
     [!code-csharp[Trin_TaskPaneBasic#2](../vsto/codesnippet/CSharp/Trin_TaskPaneBasic/ThisAddIn.cs#2)]  
  
    > [!NOTE]  
    >  Этот код связывает настраиваемую область задач с активным окном приложения. Для некоторых приложений может потребоваться изменить этот код, чтобы убедиться, что область задач отображается с другими документами или элементами в приложении. Дополнительные сведения см. в разделе [настраиваемых панелей задач](../vsto/custom-task-panes.md).  
  
## <a name="see-also"></a>См. также  
 [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)   
 [Настраиваемые области задач](../vsto/custom-task-panes.md)   
 [Пошаговое руководство по автоматизации приложения из настраиваемой области задач](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)  
  
  
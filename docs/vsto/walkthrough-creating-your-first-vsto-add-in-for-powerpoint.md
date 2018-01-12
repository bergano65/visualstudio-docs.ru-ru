---
title: "Пошаговое руководство: Создание первой надстройки VSTO для PowerPoint | Документы Microsoft"
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
- application-level add-ins [Office development in Visual Studio], creating your first project
- Office development in Visual Studio, creating your first project
- PowerPoint [Office development in Visual Studio], creating your first project
- add-ins [Office development in Visual Studio], creating your first project
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload: office
ms.openlocfilehash: eec0f2eaf7cc415e026a8427f7a881cd7ed15160
ms.sourcegitcommit: f9fbf1f55f9ac14e4e5c6ae58c30dc1800ca6cda
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/10/2018
---
# <a name="walkthrough-creating-your-first-vsto-add-in-for-powerpoint"></a>Пошаговое руководство. Создание первой надстройки VSTO для PowerPoint
  В этом пошаговом руководстве показано, как создать надстройку VSTO для Microsoft Office PowerPoint. Возможности, создаваемые в подобном решении, доступны для приложения независимо от того, какие презентации открыты. Дополнительные сведения см. в разделе [Общие сведения о разработке решений Office &#40; VSTO &#41; ](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
-   создание проекта надстройки VSTO для PowerPoint;  
  
-   написание кода, использующего объектную модель PowerPoint для добавления текстового поля в каждый новый слайд;  
  
-   Построение и запуск проекта для тестирования.  
  
-   очистка проекта для прекращения автоматического запуска надстройки VSTO на компьютере разработчика.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Предварительные требования  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   PowerPoint  
  
## <a name="creating-the-project"></a>Создание проекта  
  
#### <a name="to-create-a-new-project"></a>Создание нового проекта  
  
1.  Запустите [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  В меню **Файл** выберите пункт **Создать**, а затем команду **Проект**.  
  
3.  В области шаблонов разверните узел **Visual C#** или **Visual Basic**, а затем узел **Office/SharePoint**.  
  
4.  В развернутом узле **Office/SharePoint** выберите узел **Надстройки Office** .  
  
5.  В списке шаблонов проектов выберите шаблон проекта надстройки VSTO для PowerPoint.  
  
6.  В **имя** введите **FirstPowerPointAddIn**.  
  
7.  Нажмите кнопку **ОК**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Создает **FirstPowerPointAddIn** проект и открывает **ThisAddIn** файл исходного кода в редакторе.  
  
## <a name="writing-code-that-adds-text-to-each-new-slide"></a>Написание кода, добавляющего текст в каждый новый слайд  
 Затем добавьте код в файл ThisAddIn. Новый код использует объектную модель PowerPoint для добавления текстового поля в каждый новый слайд. По умолчанию файл кода ThisAddIn содержит следующий созданный код:  
  
-   Частичное определение класса `ThisAddIn` . Этот класс предоставляет точку входа для кода и обеспечивает доступ к объектной модели PowerPoint. Для получения дополнительной информации см. [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md). Остальная часть класса `ThisAddIn` определяется в скрытом файле кода, изменять который не следует.  
  
-   Обработчики событий `ThisAddIn_Startup` и `ThisAddIn_Shutdown` . Эти обработчики событий вызываются, когда PowerPoint загружает и выгружает надстройку VSTO. Их можно использовать для инициализации надстройки VSTO в процессе ее загрузки, а также для освобождения ресурсов, используемых вашей надстройкой VSTO при ее выгрузке. Дополнительные сведения см. в разделе [Events in Office Projects](../vsto/events-in-office-projects.md).  
  
#### <a name="to-add-a-text-box-to-each-new-slide"></a>Добавление текстового поля в каждый новый слайд  
  
1.  В файл кода ThisAddIn добавьте в класс `ThisAddIn` указанный ниже код. В коде определяется обработчик события <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide> объекта <xref:Microsoft.Office.Interop.PowerPoint.Application>.  
  
     Когда пользователь добавляет новый слайд в активную презентацию, этот обработчик событий добавляет текстовое поле в верхнюю часть нового слайда, а также добавляет в поле текст.  
  
     [!code-vb[Trin_PowerPointAddInTutorial#1](../vsto/codesnippet/VisualBasic/Trin_PowerPointAddInTutorial/ThisAddIn.vb#1)]
     [!code-csharp[Trin_PowerPointAddInTutorial#1](../vsto/codesnippet/CSharp/Trin_PowerPointAddInTutorial/ThisAddIn.cs#1)]  
  
2.  Если используется C#, добавьте в обработчик событий `ThisAddIn_Startup` указанный ниже код. Он используется для подключения обработчика событий `Application_PresentationNewSlide` к событию <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide>.  
  
     [!code-csharp[Trin_PowerPointAddInTutorial#2](../vsto/codesnippet/CSharp/Trin_PowerPointAddInTutorial/ThisAddIn.cs#2)]  
  
 Для изменения каждого нового слайда в приведенных выше примерах кода используются следующие объекты:  
  
-   Поле `Application` класса `ThisAddIn` . Поле `Application` возвращает объект <xref:Microsoft.Office.Interop.PowerPoint.Application>, который представляет текущий экземпляр PowerPoint.  
  
-   Параметр `Sld` обработчика событий для события <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide>. Параметр `Sld` — это объект <xref:Microsoft.Office.Interop.PowerPoint.Slide>, который представляет новый слайд. Дополнительные сведения см. в разделе [решения PowerPoint](../vsto/powerpoint-solutions.md).  
  
## <a name="testing-the-project"></a>Тестирование проекта  
 При построении и запуске проекта убедитесь, что текстовое поле отображается в новых слайдах, добавляемых в презентацию.  
  
#### <a name="to-test-the-project"></a>Тестирование проекта  
  
1.  Нажмите клавишу **F5** для построения и запуска проекта.  
  
     При построении проекта код компилируется в сборку, которая включается в выходную папку сборки для проекта. Visual Studio также создает ряд записей реестра, которые позволяют PowerPoint обнаружить и загрузить надстройку VSTO, и настраивает параметры безопасности на компьютере разработчика, разрешая запуск надстройки VSTO. Дополнительные сведения см. в разделе [построение решений Office](../vsto/building-office-solutions.md).  
  
2.  В PowerPoint добавьте новый слайд в активную презентацию.  
  
3.  Убедитесь, что следующий текст добавляется в новое текстовое поле в верхней части слайда.  
  
     **Этот текст добавляется с помощью кода.**  
  
4.  Закройте PowerPoint.  
  
## <a name="cleaning-up-the-project"></a>Очистка проекта  
 Завершив разработку проекта, удалите с компьютера сборку надстройки VSTO, записи реестра и параметры безопасности. В противном случае надстройка VSTO будет запускаться при каждом открытии PowerPoint на компьютере разработчика.  
  
#### <a name="to-clean-up-your-project"></a>Очистка проекта  
  
1.  В Visual Studio в меню **Построение** выберите пункт **Очистить решение**.  
  
## <a name="next-steps"></a>Следующие шаги  
 Теперь, когда вы создали базовую надстройку VSTO для PowerPoint, изучите более подробную информацию о разработке надстроек VSTO в следующих разделах:  
  
-   Общие задачи программирования, которые можно выполнять в надстройках VSTO для PowerPoint. Для получения дополнительной информации см. [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
-   Использование объектной модели PowerPoint. Дополнительные сведения см. в разделе [решения PowerPoint](../vsto/powerpoint-solutions.md).  
  
-   Настройка пользовательского интерфейса PowerPoint, например, путем добавления настраиваемой вкладки на ленту или создания собственной настраиваемой области задач. Дополнительные сведения см. в разделе [настройки пользовательского интерфейса Office](../vsto/office-ui-customization.md).  
  
-   Построение и отладка надстроек VSTO для PowerPoint. Дополнительные сведения см. в разделе [построение решений Office](../vsto/building-office-solutions.md).  
  
-   Развертывание надстроек VSTO для PowerPoint. Дополнительные сведения см. в разделе [развертывание решения Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>См. также  
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Решения PowerPoint](../vsto/powerpoint-solutions.md)   
 [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)   
 [Построение решений Office](../vsto/building-office-solutions.md)   
 [Развертывание решения Office](../vsto/deploying-an-office-solution.md)   
 [Общие сведения о шаблонах проектов Office](../vsto/office-project-templates-overview.md)  
  
  
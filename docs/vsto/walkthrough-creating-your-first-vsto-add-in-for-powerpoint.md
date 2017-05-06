---
title: "Пошаговое руководство. Создание первой надстройки VSTO для PowerPoint"
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
  - "надстройки [разработка решений Office в Visual Studio], создание первого проекта"
  - "надстройки уровня приложения [разработка решений Office в Visual Studio], создание первого проекта"
  - "Office - разработка решений в Visual Studio, создание первого проекта"
  - "PowerPoint [разработка решений Office в Visual Studio], создание первого проекта"
ms.assetid: 52d1543a-c9cb-4ee1-aa5b-90759fce9d3a
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Пошаговое руководство. Создание первой надстройки VSTO для PowerPoint
  В этом пошаговом руководстве показано, как создать надстройку VSTO для Microsoft Office PowerPoint.  Функции, создаваемые в подобном решении, доступны для приложения независимо от того, какие презентации открыты.  Дополнительные сведения см. в статье [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
-   создание проекта надстройки VSTO для PowerPoint;  
  
-   написание кода, использующего объектную модель PowerPoint для добавления текстового поля в каждый новый слайд;  
  
-   построение и запуск проекта для тестирования;  
  
-   очистка проекта для прекращения автоматического запуска надстройки VSTO на компьютере разработчика.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Обязательные компоненты  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   PowerPoint  
  
## Создание проекта  
  
#### Создание нового проекта  
  
1.  Запустите [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  В меню **Файл** выберите пункт **Создать**, а затем команду **Проект**.  
  
3.  В области шаблонов разверните узел **Visual C\#** или **Visual Basic**, а затем узел **Office\/SharePoint**.  
  
4.  В развернутом узле **Office\/SharePoint** выберите узел **Надстройки Office**.  
  
5.  В списке шаблонов проектов выберите шаблон проекта надстройки VSTO для PowerPoint.  
  
6.  В поле **Имя** введите **FirstPowerPointAddIn**.  
  
7.  Нажмите кнопку **ОК**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] создает проект **FirstPowerPointAddIn** и открывает файл кода **ThisAddIn** в редакторе.  
  
## Написание кода, добавляющего текст в каждый новый слайд  
 Добавьте код в файл кода ThisAddIn.  Новый код использует объектную модель PowerPoint для добавления текстового поля в каждый новый слайд.  По умолчанию файл кода ThisAddIn содержит следующий созданный код:  
  
-   Частичное определение класса `ThisAddIn`.  Этот класс предоставляет точку входа для кода и обеспечивает доступ к объектной модели PowerPoint.  Дополнительные сведения см. в статье [Приступая к программированию надстроек VSTO](../vsto/programming-vsto-add-ins.md).  Остальная часть класса `ThisAddIn` определяется в скрытом файле кода, изменять который не следует.  
  
-   Обработчики событий `ThisAddIn_Startup` и `ThisAddIn_Shutdown`.  Эти обработчики событий вызываются, когда PowerPoint загружает и выгружает надстройку VSTO.  Их можно использовать для инициализации надстройки VSTO в процессе ее загрузки, а также для освобождения ресурсов, используемых вашей надстройкой VSTO при ее выгрузке.  Дополнительные сведения см. в разделе [События в проектах Office](../vsto/events-in-office-projects.md).  
  
#### Добавление текстового поля в каждый новый слайд  
  
1.  В файл кода ThisAddIn добавьте указанный ниже код в класс `ThisAddIn`.  В коде определяется обработчик события <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide> объекта <xref:Microsoft.Office.Interop.PowerPoint.Application>.  
  
     Когда пользователь добавляет новый слайд в активную презентацию, этот обработчик событий добавляет текстовое поле в верхнюю часть нового слайда, а также добавляет в поле текст.  
  
     [!code-csharp[Trin_PowerPointAddInTutorial#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_PowerPointAddInTutorial/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_PowerPointAddInTutorial#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_PowerPointAddInTutorial/VB/ThisAddIn.vb#1)]  
  
2.  Если используется C\#, добавьте в обработчик событий `ThisAddIn_Startup` указанный ниже код.  Он используется для подключения обработчика событий `Application_PresentationNewSlide` к событию <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide>.  
  
     [!code-csharp[Trin_PowerPointAddInTutorial#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_PowerPointAddInTutorial/CS/ThisAddIn.cs#2)]  
  
 Для изменения каждого нового слайда в приведенных выше примерах кода используются следующие объекты:  
  
-   Поле `Application` класса `ThisAddIn`.  Поле `Application` возвращает объект <xref:Microsoft.Office.Interop.PowerPoint.Application>, который представляет текущий экземпляр PowerPoint.  
  
-   Параметр `Sld` обработчика событий для события <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.PresentationNewSlide>.  Параметр `Sld` — это объект <xref:Microsoft.Office.Interop.PowerPoint.Slide>, который представляет новый слайд.  Дополнительные сведения см. в разделе [Решения PowerPoint](../vsto/powerpoint-solutions.md).  
  
## Тестирование проекта  
 При построении и запуске проекта убедитесь, что текстовое поле отображается в новых слайдах, добавляемых в презентацию.  
  
#### Тестирование проекта  
  
1.  Нажмите клавишу **F5** для построения и запуска проекта.  
  
     При построении проекта код компилируется в сборку, которая включается в выходную папку сборки для проекта.  Visual Studio также создает ряд записей реестра, которые позволяют PowerPoint обнаружить и загрузить надстройку VSTO, и настраивает параметры безопасности на компьютере разработчика, разрешая запуск надстройки VSTO.  Дополнительные сведения см. в разделе [Построение решений Office](../vsto/building-office-solutions.md).  
  
2.  В PowerPoint добавьте новый слайд в активную презентацию.  
  
3.  Убедитесь, что следующий текст добавляется в новое текстовое поле в верхней части слайда.  
  
     **Этот текст добавляется с помощью кода.**  
  
4.  Закройте PowerPoint.  
  
## Очистка проекта  
 Завершив разработку проекта, удалите с компьютера сборку надстройки VSTO, записи реестра и параметры безопасности.  В противном случае надстройка VSTO будет запускаться при каждом открытии PowerPoint на компьютере разработчика.  
  
#### Очистка проекта  
  
1.  В Visual Studio в меню **Построение** выберите пункт **Очистить решение**.  
  
## Следующие действия  
 Теперь, когда вы создали базовую надстройку VSTO для PowerPoint, изучите более подробную информацию о разработке надстроек VSTO в следующих разделах:  
  
-   Общие задачи программирования, которые можно выполнять в надстройках VSTO для PowerPoint.  Дополнительные сведения см. в статье [Приступая к программированию надстроек VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   Использование объектной модели PowerPoint.  Дополнительные сведения см. в разделе [Решения PowerPoint](../vsto/powerpoint-solutions.md).  
  
-   Настройка пользовательского интерфейса PowerPoint, например, путем добавления настраиваемой вкладки на ленту или создания собственной настраиваемой области задач.  Дополнительные сведения см. в разделе [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md).  
  
-   Построение и отладка надстроек VSTO для PowerPoint.  Дополнительные сведения см. в разделе [Построение решений Office](../vsto/building-office-solutions.md).  
  
-   Развертывание надстроек VSTO для PowerPoint.  Дополнительные сведения см. в разделе [Развертывание решения Office](../vsto/deploying-an-office-solution.md).  
  
## См. также  
 [Приступая к программированию надстроек VSTO](../vsto/programming-vsto-add-ins.md)   
 [Решения PowerPoint](../vsto/powerpoint-solutions.md)   
 [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)   
 [Построение решений Office](../vsto/building-office-solutions.md)   
 [Развертывание решения Office](../vsto/deploying-an-office-solution.md)   
 [Общие сведения о шаблонах проектов Office](../vsto/office-project-templates-overview.md)  
  
  
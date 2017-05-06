---
title: "Пошаговое руководство. Создание первой надстройки VSTO для Project"
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
  - "надстройки уровня приложения [разработка решений Office в Visual Studio], создание первого проекта"
  - "разработка решений Office в Visual Studio, создание первого проекта"
  - "Project [разработка решений Office в Visual Studio], создание первого проекта"
  - "надстройки [разработка решений Office в Visual Studio], создание первого проекта"
ms.assetid: da2b727e-6db8-4853-bf00-7afe0ef13213
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Пошаговое руководство. Создание первой надстройки VSTO для Project
  В этом пошаговом руководстве показано, как создать надстройку VSTO для Microsoft Office Project. Функции, создаваемые в таком решении, доступны для самого приложения независимо от того, какие проекты открыты. Дополнительные сведения см. в разделе [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
-   создание проекта надстройки VSTO для Project;  
  
-   написание кода, использующего объектную модель Project для добавления задачи в новый проект;  
  
-   Построение и запуск проекта для тестирования.  
  
-   Удаление завершенного проекта для прекращения автоматического запуска надстройки VSTO на компьютере разработчика.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Обязательные компоненты  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Project_15_short](../vsto/includes/project-15-short-md.md)] или [!INCLUDE[Project_14_short](../vsto/includes/project-14-short-md.md)].  
  
## Создание проекта  
  
#### Создание проекта в Visual Studio  
  
1.  Запустите [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  В меню **Файл** выберите пункт **Создать**, а затем команду **Проект**.  
  
3.  В области шаблонов разверните узел **Visual C\#** или **Visual Basic**, а затем узел **Office\/SharePoint**.  
  
4.  В развернутом узле **Office\/SharePoint** выберите узел **Надстройки Office**.  
  
5.  В списке шаблонов проекта выберите шаблон **Надстройка Project 2010** или **Надстройка Project 2013**.  
  
6.  В поле **Имя** введите **FirstProjectAddIn**.  
  
7.  Нажмите кнопку **ОК**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] создает проект **FirstProjectAddIn** и открывает файл кода **ThisAddIn** в редакторе.  
  
## Создание кода, добавляющего новую задачу в проект  
 Добавьте код в файл кода ThisAddIn. В этом коде для добавления новой задачи в проект используется объектная модель Project. По умолчанию файл кода ThisAddIn содержит следующий созданный код:  
  
-   Частичное определение класса `ThisAddIn`. Этот класс предоставляет точку входа для кода и обеспечивает доступ к объектной модели Project. Для получения дополнительной информации см. [Приступая к программированию надстроек VSTO](../vsto/programming-vsto-add-ins.md). Остальная часть класса `ThisAddIn`определяется в скрытом файле кода, изменять который не следует.  
  
-   Обработчики событий `ThisAddIn_Startup` и `ThisAddIn_Shutdown`. Эти обработчики событий вызываются, когда Project загружает и выгружает надстройку VSTO. Их можно использовать для инициализации надстройки VSTO в процессе ее загрузки, а также для освобождения ресурсов, используемых вашей надстройкой VSTO при ее выгрузке. Для получения дополнительной информации см. [События в проектах Office](../vsto/events-in-office-projects.md).  
  
#### Добавление задачи в новый проект  
  
1.  В файл кода ThisAddIn добавьте в класс `ThisAddIn` указанный ниже код. В коде определяется обработчик события NewProject класса Microsoft.Office.Interop.MSProject.Application.  
  
     Когда пользователь создает проект, этот обработчик событий добавляет в него задачу.  
  
     [!code-csharp[Trin_ProjectAddInTutorial#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ProjectAddInTutorial/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_ProjectAddInTutorial#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ProjectAddInTutorial/VB/ThisAddIn.vb#1)]  
  
 Для изменения проекта в этом примере кода используются указанные ниже объекты.  
  
-   Поле `Application` класса `ThisAddIn`. Поле `Application` возвращает объект Microsoft.Office.Interop.MSProject.Application, который представляет текущий экземпляр Project.  
  
-   Параметр `pj` обработчика событий для события NewProject. Параметр `pj` — это объект Microsoft.Office.Interop.MSProject.Project, который представляет проект. Дополнительные сведения см. в разделе [Решения Project](../vsto/project-solutions.md).  
  
1.  Если используется C\#, добавьте в обработчик событий `ThisAddIn_Startup` указанный ниже код. Он подключает обработчик событий `Application_Newproject` к событию NewProject.  
  
     [!code-csharp[Trin_ProjectAddInTutorial#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ProjectAddInTutorial/CS/ThisAddIn.cs#2)]  
  
-  
  
## Тестирование проекта  
 Во время сборки и выполнения проекта убедитесь в том, что новая задача отображается в новом проекте.  
  
#### Тестирование проекта  
  
1.  Нажмите клавишу **F5** для построения и запуска проекта. Запускается Microsoft Project, и при этом автоматически открывается пустой проект.  
  
     При построении проекта код компилируется в сборку, которая включается в выходную папку сборки для проекта. Visual Studio также создает ряд записей реестра, которые позволяют Project обнаружить и загрузить надстройку VSTO, и настраивает параметры безопасности на компьютере разработчика, разрешая запуск надстройки VSTO. Дополнительные сведения см. в разделе [Обзор процесса сборки решения Office](http://msdn.microsoft.com/ru-ru/a9d12e4f-c9ea-4a62-a841-c42b91f831ee).  
  
2.  Убедитесь в том, что новая задача добавлена в пустой проект.  
  
3.  Убедитесь в том, что в поле **Имя задачи** виден следующий текст:  
  
     **Этот текст добавляется с помощью кода.**  
  
4.  Закройте Microsoft Project.  
  
## Очистка проекта  
 Завершив разработку проекта, удалите с компьютера сборку надстройки VSTO, записи реестра и параметры безопасности. В противном случае надстройка VSTO будет запускаться при каждом открытии Microsoft Project на компьютере разработчика.  
  
#### Очистка проекта  
  
1.  В Visual Studio в меню **Построение** выберите пункт **Очистить решение**.  
  
## Следующие действия  
 Теперь, когда вы создали базовую надстройку VSTO для Project, ознакомьтесь с более подробными сведениями о разработке надстроек VSTO в следующих разделах.  
  
-   Общие задачи программирования, которые можно выполнять в надстройках VSTO для Project: [Приступая к программированию надстроек VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   Использование объектной модели Project: [Решения Project](../vsto/project-solutions.md).  
  
-   Сборка и отладка надстроек VSTO для Project: [Построение решений Office](../vsto/building-office-solutions.md).  
  
-   Развертывание надстроек VSTO для Project: [Развертывание решения Office](../vsto/deploying-an-office-solution.md).  
  
## См. также  
 [Приступая к программированию надстроек VSTO](../vsto/programming-vsto-add-ins.md)   
 [Решения Project](../vsto/project-solutions.md)   
 [Построение решений Office](../vsto/building-office-solutions.md)   
 [Развертывание решения Office](../vsto/deploying-an-office-solution.md)   
 [Общие сведения о шаблонах проектов Office](../vsto/office-project-templates-overview.md)  
  
  
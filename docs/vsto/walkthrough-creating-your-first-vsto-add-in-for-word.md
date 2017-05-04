---
title: "Пошаговое руководство. Создание первой надстройки VSTO для Word | Microsoft Docs"
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
  - "Word [разработка решений Office в Visual Studio], создание первого проекта"
ms.assetid: 9d857be7-5c74-4303-baf4-672afc1ea397
caps.latest.revision: 55
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 51
---
# Пошаговое руководство. Создание первой надстройки VSTO для Word
  В этом вводном пошаговом руководстве показано, как создать надстройку VSTO для Microsoft Office Word.  Функции, создаваемые в таком решении, доступны для самого приложения независимо от того, какие документы открыты.  
  
 [!INCLUDE[appliesto_wdallapp](../vsto/includes/appliesto-wdallapp-md.md)]  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
-   Создание проекта надстройки VSTO для Word  
  
-   Написание кода, который использует объектную модель Word для добавления текста в документ при его сохранении.  
  
-   Построение и запуск проекта для тестирования.  
  
-   Очистка готового проекта для прекращения автоматического запуска надстройки VSTO на компьютере разработчика.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Обязательные компоненты  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## Создание проекта  
  
#### Создание нового проекта надстройки VSTO для Word в Visual Studio  
  
1.  Запустите [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  В меню **Файл** выберите пункт **Создать**, а затем команду **Проект**.  
  
3.  В области шаблонов разверните узел **Visual C\#** или **Visual Basic**, а затем узел **Office\/SharePoint**.  
  
4.  В развернутом узле **Office\/SharePoint** выберите узел **Надстройки Office**.  
  
5.  В списке шаблонов проектов выберите проект надстройки VSTO для Word.  
  
6.  В поле **Имя** введите **FirstExcelAddIn**.  
  
7.  Нажмите кнопку **ОК**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] создает проект **FirstWordAddIn** и открывает файл кода ThisAddIn в редакторе.  
  
## Написание кода для добавления текста в сохраняемый документ  
 Добавьте код в файл кода ThisAddIn.  Новый код использует объектную модель Word для добавления стандартного текста в каждый сохраненный документ.  По умолчанию файл кода ThisAddIn содержит следующий созданный код:  
  
-   Частичное определение класса `ThisAddIn`.  Этот класс предоставляет точку входа для кода и обеспечивает доступ к объектной модели Word.  Дополнительные сведения см. в разделе [Приступая к программированию надстроек VSTO](../vsto/programming-vsto-add-ins.md).  Остальная часть класса `ThisAddIn` определяется в скрытом файле кода, изменять который не следует.  
  
-   Обработчики событий `ThisAddIn_Startup` и `ThisAddIn_Shutdown`.  Эти обработчики событий вызываются, когда Excel загружает и выгружает надстройку VSTO.  Их можно использовать для инициализации надстройки VSTO в процессе ее загрузки, а также для освобождения ресурсов, используемых вашей надстройкой VSTO при ее выгрузке.  Дополнительные сведения см. в разделе [События в проектах Office](../vsto/events-in-office-projects.md).  
  
#### Добавление абзаца текста в сохраненный документ  
  
1.  В файле кода ThisAddIn добавьте в класс `ThisAddIn` указанный ниже код.  Новый код определяет обработчик событий для события <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave>, которое возникает при сохранении документа.  
  
     Когда пользователь сохраняет документ, обработчик событий добавляет новый текст в начало документа.  
  
     [!code-csharp[Trin_WordAddInTutorial#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInTutorial/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_WordAddInTutorial#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInTutorial/VB/ThisAddIn.vb#1)]  
  
    > [!NOTE]  
    >  Этот код использует значение индекса 1 для доступа к первому абзацу в коллекции <xref:Microsoft.Office.Interop.Word._Document.Paragraphs%2A>.  Хотя Visual Basic и Visual C\# используют массивы, которые начинаются с 0, нижней границей массива для большинства коллекций в объектной модели Word является 1.  Дополнительные сведения см. в разделе [Написание кода в решениях Office](../vsto/writing-code-in-office-solutions.md).  
  
2.  Если вы используете C\#, добавьте в обработчик событий `ThisAddIn_Startup` указанный ниже код.  Этот код используется для подключения обработчика событий `Application_DocumentBeforeSave` к событию <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave>.  
  
     [!code-csharp[Trin_WordAddInTutorial#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInTutorial/CS/ThisAddIn.cs#2)]  
  
 Для изменения документа при его сохранении в приведенных выше примерах кода используются следующие объекты.  
  
-   Поле `Application` класса `ThisAddIn`.  Поле `Application` возвращает объект <xref:Microsoft.Office.Interop.Word.Application>, который представляет текущий экземпляр Word.  
  
-   Параметр `Doc` обработчика событий для события <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave>.  Параметр `Doc` является объектом <xref:Microsoft.Office.Interop.Word.Document>, который представляет сохраненный документ.  Дополнительные сведения см. в разделе [Общие сведения об объектной модели Word](../vsto/word-object-model-overview.md).  
  
## Тестирование проекта  
  
#### Порядок тестирования проекта  
  
1.  Нажмите клавишу **F5** для сборки и запуска проекта.  
  
     При сборке проекта код компилируется в сборку, которая включается в выходную папку сборки для проекта.  Visual Studio также создает ряд записей реестра, которые позволяют Excel обнаружить и загрузить надстройку VSTO, и настраивает параметры безопасности на компьютере разработчика, разрешая запуск надстройки VSTO.  Дополнительные сведения см. в разделе [Построение решений Office](../vsto/building-office-solutions.md).  
  
2.  В Word сохраните активный документ.  
  
3.  Убедитесь, что в документ добавлен следующий текст.  
  
     **Этот текст был добавлен с помощью кода.**  
  
4.  Закройте Word.  
  
## Очистка проекта  
 Завершив разработку проекта, удалите с компьютера разработчика сборку надстройки VSTO, записи реестра и параметры безопасности.  В противном случае надстройка VSTO будет запускаться при каждом открытии программы Word на компьютере разработчика.  
  
#### Очистка готового проекта на компьютере разработчика  
  
1.  В Visual Studio в меню **Сборка** выберите пункт **Очистить решение**.  
  
## Следующие действия  
 Теперь, когда вы создали базовую надстройку VSTO для Word, ознакомьтесь с более подробными сведениями о разработке надстроек VSTO в следующих разделах.  
  
-   Общие задачи программирования, которые можно выполнять в надстройках VSTO: [Приступая к программированию надстроек VSTO](../vsto/programming-vsto-add-ins.md).  
  
-   Задачи программирования, характерные для надстроек VSTO для Word: [Решения Word](../vsto/word-solutions.md).  
  
-   Использование объектной модели Word: [Общие сведения об объектной модели Word](../vsto/word-object-model-overview.md).  
  
-   Настройка пользовательского интерфейса Word, например путем добавления настраиваемой вкладки на ленту или создания собственной настраиваемой области задач: [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md).  
  
-   Построение и отладка надстроек VSTO для Word: [Построение решений Office](../vsto/building-office-solutions.md).  
  
-   Развертывание надстроек VSTO для Word: [Развертывание решения Office](../vsto/deploying-an-office-solution.md).  
  
## См. также  
 [Общие сведения о разработке решений Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Решения Word](../vsto/word-solutions.md)   
 [Приступая к программированию надстроек VSTO](../vsto/programming-vsto-add-ins.md)   
 [Общие сведения об объектной модели Word](../vsto/word-object-model-overview.md)   
 [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)   
 [Построение решений Office](../vsto/building-office-solutions.md)   
 [Развертывание решения Office](../vsto/deploying-an-office-solution.md)   
 [Общие сведения о шаблонах проектов Office](../vsto/office-project-templates-overview.md)  
  
  
---
title: "Пошаговое руководство: Создание первой настройки уровня документа для Word | Документы Microsoft"
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
- Office development in Visual Studio, creating your first project
- Word [Office development in Visual Studio], creating your first project
- document-level customizations [Office development in Visual Studio], creating your first project
ms.assetid: ec9f5173-0923-4aee-985a-e760e80eaae3
caps.latest.revision: "45"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 6d732f16d6794fbe59dd6f67fa904fcee916ce69
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-your-first-document-level-customization-for-word"></a>Пошаговое руководство. Создание первой настройки уровня документа для Word
  В этом вводном пошаговом руководстве показано, как создавать настройку на уровне документа для Microsoft Office Word. Функциональные возможности, создаваемые в таком решении, доступны только в том случае, когда открыт конкретный документ. Для внесения изменений в приложение настройку на уровне документа использовать нельзя (например, для отображения новой вкладки ленты, когда открыт любой документ).  
  
 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]  
  
 В данном пошаговом руководстве рассмотрены следующие задачи:  
  
-   Создание проекта документа Word.  
  
-   Добавление текста в документ, который размещен в конструкторе Visual Studio.  
  
-   Написание кода, использующего объектную модель Word для добавления текста в настраиваемый документ при его открытии.  
  
-   Сборка и запуск проекта для тестирования.  
  
-   Очистка проекта для удаления ненужных файлов сборки и параметров безопасности на компьютере разработчика.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Предварительные требования  
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   Microsoft Word  
  
## <a name="creating-the-project"></a>Создание проекта  
  
#### <a name="to-create-a-new-word-document-project-in-visual-studio"></a>Создание нового проекта документа Word в Visual Studio  
  
1.  Запустите [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  В меню **Файл** выберите пункт **Создать**, а затем команду **Проект**.  
  
3.  В области шаблонов разверните узел **Visual C#** или **Visual Basic**, а затем узел **Office/SharePoint**.  
  
4.  В развернутом узле **Office/SharePoint** выберите узел **Надстройки Office** .  
  
5.  В списке шаблонов проектов выберите проект документа VSTO для Word.  
  
6.  В **имя** введите **FirstDocumentCustomization**.  
  
7.  Нажмите кнопку **ОК**.  
  
     Откроется **Мастер проектов набора средств Visual Studio для Office** .  
  
8.  Выберите **создания документа**и нажмите кнопку **ОК**.  
  
     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Создает **FirstDocumentCustomization** проекта, а также добавляет **FirstDocumentCustomization** документа и файл кода ThisDocument в проект. **FirstDocumentCustomization** документ автоматически открывается в конструкторе.  
  
## <a name="closing-and-reopening-the-document-in-the-designer"></a>Закрытие и повторное открытие документа в конструкторе  
 Если вы случайно или преднамеренно закрыли документ в конструкторе во время разработки проекта, его можно снова открыть.  
  
#### <a name="to-close-and-reopen-the-document-in-the-designer"></a>Закрытие и повторное открытие документа в конструкторе  
  
1.  Закрыть документ, щелкнув **закрыть** кнопку (X) в окне конструктора.  
  
2.  В **обозревателе решений**, щелкните правой кнопкой мыши **ThisDocument** файл кода, а затем нажмите кнопку **конструктор представлений**.  
  
     \- или -  
  
     В **обозревателе решений**, дважды щелкните **ThisDocument** файл кода.  
  
## <a name="adding-text-to-the-document-in-the-designer"></a>Добавление текста в документ в конструкторе  
 Для разработки пользовательского интерфейса настройки можно изменить документ, который открыт в конструкторе. Например, можно добавить текст, таблицы или элементы управления Word. Дополнительные сведения об использовании конструктора см. в разделе [проекты Office в среде Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md).  
  
#### <a name="to-add-text-to-your-document-by-using-the-designer"></a>Добавление текста в документ с помощью конструктора  
  
1.  В документе, который открыт в конструкторе, введите следующий текст.  
  
     **Этот текст добавляется с помощью конструктора.**  
  
## <a name="adding-text-to-the-document-programmatically"></a>Добавление текста в документ программным способом  
 Добавьте код в файл кода ThisDocument. Новый код использует объектную модель Word для добавления второго абзаца текста в документ. По умолчанию файл кода ThisDocument содержит следующий созданный код:  
  
-   Частичное определение класса `ThisDocument`, который представляет модель программирования документа и предоставляет доступ к объектной модели Word. Дополнительные сведения см. в разделе [ведущий элемент документа](../vsto/document-host-item.md) и [Общие сведения о модели объектов Word](../vsto/word-object-model-overview.md). Остальная часть класса `ThisDocument`определяется в скрытом файле кода, изменять который не следует.  
  
-   Обработчики событий `ThisDocument_Startup` и `ThisDocument_Shutdown`. Эти обработчики событий вызываются при открытии и закрытии документа. Эти обработчики событий следует использовать для инициализации своей настройки при открытии документа и для освобождения ресурсов, применяемых настройкой, при закрытии документа. Дополнительные сведения см. в разделе [Events in Office Projects](../vsto/events-in-office-projects.md).  
  
#### <a name="to-add-a-second-paragraph-of-text-to-the-document-by-using-code"></a>Добавление второго абзаца текста в документ с помощью кода  
  
1.  В **обозревателе решений**, щелкните правой кнопкой мыши **ThisDocument**, а затем нажмите кнопку **Просмотр кода**.  
  
     Файл кода открывается в Visual Studio.  
  
2.  Замените обработчик событий `ThisDocument_Startup` следующим кодом. При открытии документа этот код добавляет второй абзац текста в документ.  
  
     [!code-vb[Trin_WordDocumentTutorial#1](../vsto/codesnippet/VisualBasic/FirstDocumentCustomization/ThisDocument.vb#1)]
     [!code-csharp[Trin_WordDocumentTutorial#1](../vsto/codesnippet/CSharp/FirstDocumentCustomization/ThisDocument.cs#1)]  
  
    > [!NOTE]  
    >  Этот код использует значение индекса 1 для доступа к первому абзацу в свойстве <xref:Microsoft.Office.Tools.Word.Document.Paragraphs%2A>. Хотя Visual Basic и Visual C# используют массивы, которые начинаются с 0, нижней границей массива для большинства коллекций в объектной модели Word является 1. Для получения дополнительной информации см. [Writing Code in Office Solutions](../vsto/writing-code-in-office-solutions.md).  
  
## <a name="testing-the-project"></a>Тестирование проекта  
  
#### <a name="to-test-your-document"></a>Проверка документа  
  
1.  Нажмите клавишу **F5** для построения и запуска проекта.  
  
     При построении проекта код компилируется в сборку, которая связана с документом. Visual Studio помещает копию документа и сборку в выходную папку сборки для проекта и настраивает параметры безопасности на компьютере разработчика, чтобы разрешить выполнение настройки. Дополнительные сведения см. в разделе [построение решений Office](../vsto/building-office-solutions.md).  
  
2.  Убедитесь, что в документе отображается следующий текст.  
  
     **Этот текст добавляется с помощью конструктора.**  
  
     **Этот текст добавляется с помощью кода.**  
  
3.  Закройте документ.  
  
## <a name="cleaning-up-the-project"></a>Очистка проекта  
 После завершения разработки проекта следует удалить файлы в выходной папке сборки и параметры безопасности, созданные в процессе сборки.  
  
#### <a name="to-clean-up-the-completed-project-on-your-development-computer"></a>Очистка завершенного проекта на компьютере разработчика  
  
1.  В Visual Studio в меню **Построение** выберите пункт **Очистить решение**.  
  
## <a name="next-steps"></a>Следующие шаги  
 Теперь после создания базовой настройки на уровне документа для Word в следующих разделах можно ознакомиться с процессом разработки настроек:  
  
-   Общие задачи программирования, которые можно выполнять в настройках на уровне документа: [программирование настроек на уровне документа](../vsto/programming-document-level-customizations.md).  
  
-   Задачи программирования, характерные для настроек на уровне документа для Word: [решений Word](../vsto/word-solutions.md).  
  
-   С помощью объектной модели Word: [Общие сведения о модели объектов Word](../vsto/word-object-model-overview.md).  
  
-   Настройка пользовательского интерфейса Word, например добавление настраиваемой вкладки на ленту или создания собственной панели действий: [настройки пользовательского интерфейса Office](../vsto/office-ui-customization.md).  
  
-   С помощью расширенных объектов Word, предоставляемых решениями Office в Visual Studio для выполнения задач, которые невозможно выполнить с помощью объектной модели Word (например, размещение управляемых элементов управления в документах и привязка элементов управления Word к данным с помощью данных Windows Forms Привязка модели): [автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md).  
  
-   Построение и отладка настроек на уровне документа для Word: [построение решений Office](../vsto/building-office-solutions.md).  
  
-   Развертывание настроек на уровне документа для Word: [развертывание решения Office](../vsto/deploying-an-office-solution.md).  
  
## <a name="see-also"></a>См. также  
 [Общие сведения о разработке решений Office &#40; VSTO &#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Решения Word](../vsto/word-solutions.md)   
 [Программирование настроек на уровне документа](../vsto/programming-document-level-customizations.md)   
 [Общие сведения об объектной модели Word](../vsto/word-object-model-overview.md)   
 [Автоматизация Word с помощью расширенных объектов](../vsto/automating-word-by-using-extended-objects.md)   
 [Настройка пользовательского интерфейса Office](../vsto/office-ui-customization.md)   
 [Построение решений Office](../vsto/building-office-solutions.md)   
 [Развертывание решения Office](../vsto/deploying-an-office-solution.md)   
 [Общие сведения о шаблонах проектов Office](../vsto/office-project-templates-overview.md)  
  
  
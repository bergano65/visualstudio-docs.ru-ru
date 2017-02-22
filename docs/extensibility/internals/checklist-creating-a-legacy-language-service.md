---
title: "Контрольный список: Создание языковую службу для прежних версий | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "языковые службы"
  - "языковые службы, машинный код"
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Контрольный список: Создание языковую службу для прежних версий
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Следующий контрольный список приведены основные необходимо выполнить для создания службы языка [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] редактор.  Интегрировать службы языка [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]необходимо создать средство оценки выражений отладки.  Дополнительные сведения см. в разделе [Написание вычислитель выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) в  [Расширение возможностей отладчика Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md).  
  
## Этапы создания службы языка  
  
1.  Реализуйте интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>.  
  
    -   Реализуйте в VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> интерфейс, чтобы предоставить службу языка.  
  
    -   Внесите в доступный языковой службы в интегрированной среде разработки \(ide\) в вашем <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> реализация.  
  
2.  Реализуйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> интерфейс в главном классе службы языка.  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> интерфейс начальная точка взаимодействия между редактором языка основной и службой.  
  
### Дополнительные функции  
 Следующие функции являются необязательными и могут быть реализованы в любом порядке.  Эти функции расширяют функциональность службы языка.  
  
-   Расцветка синтаксиса  
  
     Реализуйте интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>.  Реализация этого интерфейса, если данные средства синтаксического анализа возвращают соответствующие данные о цвете.  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> метод возвращает  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> интерфейс.  Отдельный экземпляр colorizer создается для каждого текстового буфера, поэтому необходимо реализовать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> интерфейс отдельно.  Дополнительные сведения см. в разделе [Синтаксиса в языковую службу для прежних версий](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
-   Окно кода  
  
     Реализуйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> интерфейс, чтобы разрешить языковую службу, чтобы получать уведомления, когда новое окно кода будет создано.  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> метод возвращает  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> интерфейс.  Служба языка может затем добавить специальный пользовательский интерфейс в окно кода in <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>.  Языковую службу также может выполнять все специальные обработки, как добавить фильтр представления текста внутри <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A>.  
  
-   Фильтр представления текста  
  
     Чтобы обеспечить завершение выписки IntelliSense в службе языка, следует перехватывать некоторых команд, представление текста в противном случае отрегулировало мере.  Чтобы перехватывать эти команды, выполните следующие шаги:  
  
    -   Реализуйте <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> участвовать в командах редактора цепочки и маркеров команды.  
  
    -   Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> метод и передайте ваше  <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> реализация.  
  
    -   Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A> метод при наконец удалите из представления так, чтобы эти команды больше не передаются.  
  
     Команды, которые должны быть обработаны, зависит от службы, предоставляемые.  Дополнительные сведения см. в разделе [Важные команды для фильтров службы языка](../../extensibility/internals/important-commands-for-language-service-filters.md).  
  
    > [!NOTE]
    >  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> интерфейс должен быть реализован в одном объекте как  <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс.  
  
-   Завершение операторов  
  
     Реализуйте интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>.  
  
     Поддержка команды завершения выписки \(т е <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> \) и вызовите  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> метод  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> интерфейс передачи  <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>интерфейс.  Дополнительные сведения см. в разделе [Завершение операторов в языковую службу для прежних версий](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).  
  
-   Советы метода  
  
     Реализуйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> интерфейс, чтобы предоставить сведения для метода наклоняет окно.  
  
     Установите фильтр представления текста для обработки команд, так что известно, если отображение окна окна подсказок по данным методом.  Дополнительные сведения см. в разделе [Сведения о параметрах в языковую службу для прежних версий](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).  
  
-   Метки ошибки  
  
     Реализуйте интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>.  
  
     Создайте объекты метки ошибки, которые реализуют <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> интерфейс и вызывает  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> метод передачи  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> интерфейс объекта метки ошибки.  
  
     Обычно каждая метка ошибки управляет элементом в окне список задач.  
  
-   Элементы списка задач  
  
     Реализуйте предоставления класса элемента задачи <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> интерфейс.  
  
     Реализуйте предоставления класса поставщика задачи <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> интерфейс и  <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> интерфейс.  
  
     Реализуйте предоставления класса перечислителя задачи <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> интерфейс.  
  
     Регистрация поставщика задачи со списком задач <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> метод.  
  
     Получите <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> интерфейс путем вызова поставщик услуг языковой службы с идентификатором GUID службы  <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>.  
  
     Создание объектов элементов задачи и вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> метод  <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> интерфейс, когда новые или обновленные задачи.  
  
-   Элементы задачи комментариев  
  
     Используйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> интерфейс и  <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> интерфейс для получения токены задачи комментариев.  
  
     Получите <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> интерфейс из  <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> служба.  
  
     Получите <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> интерфейс из  <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> метод.  
  
     Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents> интерфейс для прослушивания изменений в списке токена.  
  
-   Структуризация  
  
     Несколько параметров для поддержки структура.  Например, можно поддерживать **Свернуть в определения** команда предоставляет редактор\-контролируемые структурные области или поддерживает клиент\-контролируемые области.  Дополнительные сведения см. в разделе [Практическое руководство: обеспечивают расширенную поддержку создания структуры в языковую службу для прежних версий](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md).  
  
-   Регистрация службы языка  
  
     Дополнительные сведения о том, как зарегистрировать службу языка см. в разделе [Регистрация службы языка для прежних версий](../../extensibility/internals/registering-a-legacy-language-service2.md) и  [Управление пакеты VSPackage](../../extensibility/managing-vspackages.md).  
  
-   Контекстная справка  
  
     Реализуйте контекст редактор одним из следующих способов:  
  
    -   Предоставляет контекст для меток текста путем реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> интерфейс.  
  
 Обеспечьте полный контекст пользователя с помощью реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> интерфейс.  
  
## См. также  
 [Разработка службы языка](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Написание вычислитель выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
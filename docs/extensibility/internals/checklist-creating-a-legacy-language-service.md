---
title: "Контрольный список: Создание языковую службу прежних версий | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services
- language services, native code
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5c06d246f7467e19969075537f321061463d1755
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="checklist-creating-a-legacy-language-service"></a>Контрольный список: Создание языковую службу прежних версий
Следующий контрольный список перечислены основные шаги, необходимые для создания службы языка для [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] базового редактора. Чтобы интегрировать в службы языка [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], необходимо создать средство оценки выражений отладки. Дополнительные сведения см. в разделе [написания выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) в [расширения отладчика Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md).  
  
## <a name="steps-for-creating-a-language-service"></a>Действия по созданию языковой службы  
  
1.  Реализовать интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>.  
  
    -   В пакете VSPackage, реализовывать <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> интерфейс для предоставления языковой службы.  
  
    -   Доступность службы языка для интегрированную среду разработки (IDE) в вашей <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> реализации.  
  
2.  Реализуйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> интерфейса в классе службы основного языка.  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Интерфейс является отправной точкой взаимодействия между базового редактора и языковой службы.  
  
### <a name="optional-features"></a>Дополнительные функции  
 Следующие функции являются необязательными и могут быть реализованы в любом порядке. Эти возможности расширения функциональности службы языка.  
  
-   Цветовая подсветка синтаксиса  
  
     Реализовать интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>. Реализации этого интерфейса должны сведения синтаксического анализа для возврата сведений соответствующий цвет.  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> Возвращает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> интерфейса. Экземпляр отдельные colorizer создается для каждого буфера текста, поэтому вам следует реализовать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> интерфейс отдельно. Дополнительные сведения см. в разделе [цветовой подсветки синтаксиса в языковую службу прежних версий](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
-   Окно кода  
  
     Реализуйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> интерфейс, позволяющий службе языка для получения уведомлений о при создании нового окна кода.  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> Возвращает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> интерфейса. Языковая служба затем можно добавить в окно кода в специальный пользовательский Интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>. Служба языка можно также сделать специальной обработки, таких как добавление фильтра представления текста в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A>.  
  
-   Фильтр представления текста  
  
     Чтобы обеспечить завершение операторов IntelliSense в языковую службу, должен перехватывать некоторые команды, представления текста, в противном случае будет обрабатываться. Чтобы перехватывать эти команды, выполните следующие действия:  
  
    -   Реализуйте <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> участвовать в команды цепочки и дескриптор команд редактора.  
  
    -   Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> метод и передайте его в ваш <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> реализации.  
  
    -   Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A> метод при отсоединении от представления, чтобы вам больше не передаются этих команд.  
  
     Команды, которые должны быть обработаны зависящие от служб, предоставляемых. Дополнительные сведения см. в разделе [важные команды для фильтров службы языка](../../extensibility/internals/important-commands-for-language-service-filters.md).  
  
    > [!NOTE]
    >  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> На тот же объект должен быть реализован интерфейс <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс.  
  
-   Завершение операторов  
  
     Реализовать интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>.  
  
     Поддерживает команду завершения инструкции (т. е <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>) и вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> метод в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> интерфейс, передав <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> интерфейса. Дополнительные сведения см. в разделе [завершение операторов в языковую службу прежних версий](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).  
  
-   Метод советы  
  
     Реализуйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> интерфейс для предоставления данных для окна подсказки метода.  
  
     Установите фильтр представления текста для обработки команд, соответствующим образом, чтобы знать, когда следует отобразить окно подсказки данных метода. Дополнительные сведения см. в разделе [сведения о параметрах в языковую службу прежних версий](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).  
  
-   Маркеры ошибок  
  
     Реализовать интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>.  
  
     Ошибка создания маркера объекты, реализующие <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> интерфейс и вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> метод, передавая <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> интерфейс объекта error маркера.  
  
     Обычно каждый маркер ошибки управляет элемент в окне списка задач.  
  
-   Элементы списка задач  
  
     Реализовать предоставления класса задачи элемент <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> интерфейса.  
  
     Реализовать предоставления класса задачи поставщика <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> интерфейс и <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> интерфейса.  
  
     Реализовать предоставления класса задачи перечислитель <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> интерфейса.  
  
     Зарегистрировать поставщик задач в списке задач <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> метод.  
  
     Получить <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> интерфейса путем вызова языковой службы поставщика услуг с GUID службой <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>.  
  
     Создайте объекты элемента задачи и вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> метод в <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> интерфейс есть новые или обновленные задачи.  
  
-   Элементы задач комментария  
  
     Используйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> интерфейс и <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> интерфейс для получения комментарий токены задач.  
  
     Получить <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> интерфейс из <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> службы.  
  
     Получить <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> интерфейс из <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> метод.  
  
     Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents> интерфейс, чтобы отслеживать изменения в список лексем.  
  
-   структуризация  
  
     Существует несколько вариантов для поддержки структурирования. Например, можно поддерживать **свернуть в определения** команды, укажите контролируемые редактор структурные области или поддержки областей, управляемая клиентом. Дополнительные сведения см. в разделе [как: предоставляют развернут структурирование поддержки в службе языка прежних версий](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md).  
  
-   Регистрация службы языка  
  
     Дополнительные сведения о регистрации служба языка см. в разделе [регистрации службы языка для прежних версий](../../extensibility/internals/registering-a-legacy-language-service2.md) и [управления пакеты VSPackage](../../extensibility/managing-vspackages.md).  
  
-   Контекстная справка  
  
     Предоставляет контекст для редактора в одном из следующих способов:  
  
    -   Предоставляют контекст для текстовых маркеров, реализовав <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> интерфейса.  
  
 Предоставьте все контекст пользователя путем реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> интерфейса.  
  
## <a name="see-also"></a>См. также  
 [Разработке службы языка для прежних версий](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Написание выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)
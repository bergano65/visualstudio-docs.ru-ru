---
title: 'Контрольный список: Создание языковой службы прежних версий | Документация Майкрософт'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- language services
- language services, native code
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7d45ad596b3aaea97773eb06b2e853d6c628ca97
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/23/2018
ms.locfileid: "49816668"
---
# <a name="checklist-creating-a-legacy-language-service"></a>Контрольный список. Создание языковой службы прежних версий
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Следующий контрольный список перечислены основные шаги, необходимые для создания службы языка для [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] базовым редактором. Чтобы интегрировать службы языка в [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], необходимо создать средство оценки выражений отладки. Дополнительные сведения см. в разделе [записи вычислитель выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) в [расширения отладчика Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md).  
  
## <a name="steps-for-creating-a-language-service"></a>Инструкции по созданию языковой службы  
  
1.  Реализовать интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>.  
  
    -   В пакете VSPackage, реализовывать <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> интерфейс, чтобы предоставить службе языка.  
  
    -   Опубликовать службу языка в интегрированной среде разработки (IDE) в вашей <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> реализации.  
  
2.  Реализуйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> интерфейса в классе службы основного языка.  
  
     <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> Интерфейс является начальной точкой взаимодействия между базовым редактором и языковой службы.  
  
### <a name="optional-features"></a>Дополнительные компоненты  
 Следующие функции являются необязательными и могут быть реализованы в любом порядке. Эти функции расширения функциональных возможностей службы вашего языка.  
  
- Цветовая подсветка синтаксиса  
  
   Реализовать интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>. Реализации этого интерфейса должны сведения средство синтаксического анализа для возврата сведений соответствующий цвет.  
  
   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> Возвращает метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> интерфейс. В отдельном палитры экземпляр создается для каждого текстового буфера, поэтому следует реализовать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> интерфейс отдельно. Дополнительные сведения см. в разделе [цветовой подсветки синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
- Окно кода  
  
   Реализуйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> интерфейс, позволяющий службе языка получать уведомления об при создании нового окна кода.  
  
   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> Возвращает метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> интерфейс. Языковая служба затем можно добавить в окно кода в специальный пользовательский Интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A>. Языковая служба также можно сделать специальной обработки, таких как добавление фильтр представления текста в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A>.  
  
- Фильтр представления текста  
  
   Чтобы обеспечить завершение операторов IntelliSense в языковую службу, должен перехватывать некоторые команды, которые бы в противном случае обработки представления текста. Чтобы перехватывать эти команды, выполните следующие действия:  
  
  - Реализуйте <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> участвовать в команды цепочки и дескриптор команд редактора.  
  
  - Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> метод и передать ваш <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> реализации.  
  
  - Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A> метод при отсоединении из представления, чтобы эти команды больше не передаются для вас.  
  
    Команды, которые должны быть обработаны зависят от служб, предоставляемых. Дополнительные сведения см. в разделе [важные команды для фильтров языковой службы](../../extensibility/internals/important-commands-for-language-service-filters.md).  
  
  > [!NOTE]
  >  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> Интерфейс должен быть реализован на один и тот же объект как <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс.  
  
- Завершение операторов  
  
   Реализовать интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>.  
  
   Поддерживает команду завершения инструкции (то есть <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>) и вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> метод в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> интерфейса, передавая <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> интерфейс. Дополнительные сведения см. в разделе [завершение операторов в языковой службе прежних версий](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).  
  
- Метод советы  
  
   Реализуйте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> интерфейс для предоставления данных для окна подсказки метода.  
  
   Установите фильтр представления текста для обработки команд соответствующим образом, вы узнаете, когда Показывать окно подсказки метода данных. Дополнительные сведения см. в разделе [сведения о параметрах в языковой службе прежних версий](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md).  
  
- Маркеры ошибок  
  
   Реализовать интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>.  
  
   Ошибка при создании маркера объекты, реализующие <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> интерфейс и вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> , передавая <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> интерфейс объекта error маркера.  
  
   Обычно каждый маркер ошибок управляет элемент в окне списка задач.  
  
- Элементы списка задач  
  
   Реализовать предоставляя класс задачи элемент <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> интерфейс.  
  
   Реализовать предоставляя класс задачи поставщика <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> интерфейс и <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> интерфейс.  
  
   Реализовать предоставляя класс задачи перечислитель <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> интерфейс.  
  
   Регистрация поставщика задач со списком задач <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> метод.  
  
   Получить <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> интерфейс путем вызова поставщика услуг службе языка в службе GUID <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>.  
  
   Создайте объекты элемента задачи и вызовите <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> метод в <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> интерфейс появились новые или обновленные задачи.  
  
- Элементы задачи комментариев  
  
   Используйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> интерфейс и <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> интерфейс для получения токенов задач комментариев.  
  
   Получить <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> интерфейс из <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> службы.  
  
   Получить <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> интерфейс из <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> метод.  
  
   Реализуйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents> интерфейс для прослушивания изменений в список лексем.  
  
- структуризация  
  
   Существует несколько вариантов для поддержки структуры. Например, можно поддерживать **свернуть в определения** команды, укажите редактором структурные области или поддержки областей, управляемое клиентом. Дополнительные сведения см. в разделе [как: укажите расширен структурирование поддержки в языковой службе прежних версий](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md).  
  
- Регистрация языковой службы  
  
   Дополнительные сведения о том, как зарегистрировать службу языка, см. в разделе [регистрация языковой службы прежних](../../extensibility/internals/registering-a-legacy-language-service2.md) и [пакеты VSPackage, управление](../../extensibility/managing-vspackages.md).  
  
- Контекстная справка  
  
   Предоставить контекст в редактор в одном из следующих способов:  
  
  -   Задать контекст для меток текста, можно реализовать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> интерфейс.  
  
  Задать все контекста пользователя, можно реализовать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> интерфейс.  
  
## <a name="see-also"></a>См. также  
 [Разработка языковой службы прежних версий](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Запись вычислителя выражений CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)


---
title: 'Контрольный список: Создание унаследованных языковых служб (ru) Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services
- language services, native code
ms.assetid: 8b73b341-a33a-4ab5-9390-178c9e563d2d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11785dab63cbb6a95ab2d34c5edbfb4525ebf34c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709787"
---
# <a name="checklist-create-a-legacy-language-service"></a>Контрольный список: Создание устаревшей языковой службы
Следующий контрольный список обобщает основные шаги, которые [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] необходимо предпринять для создания языковой службы для основного редактора. Чтобы интегрировать языковую [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]службу в систему, необходимо создать оценщика выражения отладки. Для получения дополнительной информации [см. Напишите оценщика выражения CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md) в [расширяемости отладки Visual Studio.](../../extensibility/debugger/visual-studio-debugger-extensibility.md)

## <a name="steps-to-create-a-language-service"></a>Шаги по созданию языковой службы

1. Реализуйте интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage>.

    - В VSPackage внедрить <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> интерфейс для предоставления языковой службы.

    - Сделайте свой языковой сервис доступным для интегрированной <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> среды разработки (IDE) в вашей реализации.

2. Реализация <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> интерфейса в основном классе языкового обслуживания.

     Интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> является отправной точкой взаимодействия между основным редактором и языковой службой.

### <a name="optional-features"></a>Дополнительные функции
 Следующие функции не являются обязательными и могут быть реализованы в любом порядке. Эти функции повышают функциональность вашего языкового сервиса.

- Цветовая подсветка синтаксиса

  Реализуйте интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>. Ваша реализация этого интерфейса должна иметь информацию о parser, чтобы вернуть соответствующую цветовую информацию.

  Метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> возвращает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> интерфейс. Для каждого буфера текста создается отдельный экземпляр <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> colorizer, поэтому следует реализовать интерфейс отдельно. Для получения дополнительной информации смотрите [раскраску Syntax в устаревшем языковом сервисе.](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

- Окно кода

  Реализация <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> интерфейса для получения языковой службой уведомления о создании нового окна кода.

  Метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> возвращает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> интерфейс. Языковая служба может добавить специальный uI в окне кода в. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.AddAdornments%2A> Языковая служба также может выполнять любую специальную обработку, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager.OnNewView%2A>например, добавляя фильтр представления текста.

- Фильтр представления текста

  Чтобы обеспечить завершение оператора IntelliSense в языковой службе, необходимо перехватить некоторые команды, которые в противном случае было бы обработано текстовым представлением. Чтобы перехватить эти команды, выполните следующие шаги:

  - Реализация <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> для участия в цепочке команд и обработки команд редактора.

  - Вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> метода и <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> пройти в вашей реализации.

  - Вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.RemoveCommandFilter%2A> метода, когда вы отсоедините от представления, так что эти команды больше не передаются вам.

  Команды, которые должны быть обработаны, зависят от предоставляемых услуг. Для получения дополнительной [информации см.](../../extensibility/internals/important-commands-for-language-service-filters.md)

  > [!NOTE]
  > Интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> должен быть реализован на том <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> же объекте, что и интерфейс.

- Завершение операторов

  Реализуйте интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>.

  Поддерживайте команду завершения оператора <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>(т.е. ) и вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> метод в интерфейсе, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> передавая <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> интерфейс. Для получения дополнительной информации смотрите [завершение заявления в устаревшей языковой службе](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md).

- Советы по методу

  Реализация <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> интерфейса для предоставления данных для окна наконечника метода.

  Установите фильтр представления текста для обработки команд надлежащим образом, чтобы вы знали, когда следует показать окно наконечника данных метода. Для получения дополнительной информации [см. Информация о параметре в устаревшей языковой службе.](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

- Маркеры ошибок

  Реализуйте интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>.

  Создайте объекты маркера <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> ошибок, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines.CreateLineMarker%2A> которые реализуют интерфейс и вызывают метод, проходя <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> интерфейс объекта маркера ошибки.

  Обычно каждый маркер ошибки управляет элементом в окне списка задач.

- Элементы списка задач

  Реализация класса элементов <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskItem> задач, обеспечивающего интерфейс.

  Реализация класса поставщика задач, обеспечивающего <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider> интерфейс и <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskProvider2> интерфейс.

  Реализация класса перечисления задач, <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumTaskItems> обеспечивающего интерфейс.

  Зарегистрируйте поставщика задач методом <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RegisterTaskProvider%2A> списка задач.

  Получите <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> интерфейс, позвонив поставщику услуг языковой службы с помощью GUID. <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList>

  Создавайте объекты элемента задачи и вызывайте <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList.RefreshTasks%2A> метод в интерфейсе <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskList> при походе новых или обновленных задач.

- Элементы задач комментариев

  Используйте <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> и интерфейс для получения токенов задач комментариев.

  Получите <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo> интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.SVsTaskList> от службы.

  Получите <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumCommentTaskTokens> интерфейс <xref:Microsoft.VisualStudio.Shell.Interop.IVsCommentTaskInfo.EnumTokens%2A> от метода.

  Реализация <xref:Microsoft.VisualStudio.Shell.Interop.IVsTaskListEvents> интерфейса для прослушивания изменений в списке маркеров.

- Структуризация

  Существует несколько вариантов поддержки с изложением. Например, можно поддерживать команду **«Обюги к определениям»,** предоставлять регионы контуров, контролируемых редакторами, или поддерживать регионы, контролируемые клиентами. Для получения дополнительной информации [см. Как: Предоставьте расширенную поддержку в устаревшей языковой службе.](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

- Регистрация языковых услуг

  Для получения дополнительной информации о том, как зарегистрировать [Manage VSPackages](../../extensibility/managing-vspackages.md)языковую службу, [см.](../../extensibility/internals/registering-a-legacy-language-service2.md)

- Чувствительная справка, чувствительная к контексту

  Предоставьте контекст редактору одним из следующих способов:

  - Предоставьте контекст для текстовых <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider> маркеров путем реализации интерфейса.

  - Предоставьте весь пользовательский <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageContextProvider> контекст, реализовав интерфейс.

## <a name="see-also"></a>См. также
- [Разработка устаревшего языкового сервиса](../../extensibility/internals/developing-a-legacy-language-service.md)
- [Написать оценщика экспрессии CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)

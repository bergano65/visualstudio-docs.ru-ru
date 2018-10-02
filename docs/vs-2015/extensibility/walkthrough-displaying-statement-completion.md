---
title: 'Пошаговое руководство: Отображение завершения операторов | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
caps.latest.revision: 37
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9d7cd7a1ea3ffa3fd85cbe8ed7088347298f849c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47572945"
---
# <a name="walkthrough-displaying-statement-completion"></a>Пошаговое руководство. Отображение завершения операторов
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Пошаговое руководство: отображение завершения операторов](https://docs.microsoft.com/visualstudio/extensibility/walkthrough-displaying-statement-completion).  
  
Завершение операторов на основе языка можно реализовать путем определения идентификаторов, для которых вы хотите предоставить завершения и затем активировать сеанс завершения. Можно определить завершение операторов в контексте языковой службы, определите расширение имени файла и тип содержимого и затем отобразить завершение только этого типа, или вы можете активировать завершение существующий тип контента, например, «обычный текст». В этом пошаговом руководстве показано, как требуется активировать завершение операторов для типа содержимого «обычный текст», который является типом содержимого текстовых файлов. Тип содержимого «text» является предком всех других типов содержимого, включая код и XML-файлы.  
  
 Завершение операторов обычно запускается вводя некоторые символы, например, введя начале идентификатора, такого как «использование». Обычно оно закрывается, нажав клавишу ПРОБЕЛ, Tab или ввод, чтобы зафиксировать выделения. Можно реализовать функции IntelliSense, которые запускаются, введя символ с помощью обработчика команды клавиш ( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс) и поставщика обработчик, который реализует <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> интерфейс. Для создания источника завершения, которая является список идентификаторов, которые участвуют в завершении, реализовать <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> интерфейс и версиями завершения ( <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> интерфейс). Поставщики являются составные части Managed Extensibility Framework (MEF). Они отвечают за импорт служб и брокеров и экспорт классов источника и контроллер — например, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, который позволяет осуществлять переходы в текстовом буфере и <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, что инициирует сеанс завершения.  
  
 В этом пошаговом руководстве показано, как реализовать завершение операторов с жестко набор идентификаторов. В полной реализации языковой службы и документацию по языку несут ответственность за предоставление этого содержимого.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не следует устанавливать пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Создание проекта MEF  
  
#### <a name="to-create-a-mef-project"></a>Создание проекта MEF  
  
1.  Создайте проект VSIX C#. (В **новый проект** диалоговом окне выберите **Visual C# / Extensibility**, затем **проект VSIX**.) Назовите решение `CompletionTest`.  
  
2.  Добавьте в проект шаблон элемента классификатора редактора. Дополнительные сведения см. в разделе [создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Удалите файлы существующих классов.  
  
4.  Добавьте следующие ссылки в проект и убедитесь, что **CopyLocal** присваивается `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.Shell.Immutable.10.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## <a name="implementing-the-completion-source"></a>Реализация источника завершения  
 Источник завершения отвечает за сбор набор идентификаторов и добавления содержимого в окне завершения, когда пользователь вводит триггер завершения, например первые буквы идентификатора. В этом примере, идентификаторы и их описания жестко запрограммированы в <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> метод. В большинстве случаев реального мира используется средство синтаксического анализа языка для получения маркеров для заполнения списка завершения.  
  
#### <a name="to-implement-the-completion-source"></a>Для реализации источник завершения  
  
1.  Добавьте файл класса и назовите его `TestCompletionSource`.  
  
2.  Добавьте эти объекты импорта:  
  
     [!code-csharp[VSSDKCompletionTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#1)]
     [!code-vb[VSSDKCompletionTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#1)]  
  
3.  Измените объявление класса для `TestCompletionSource` таким образом, <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>:  
  
     [!code-csharp[VSSDKCompletionTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#2)]
     [!code-vb[VSSDKCompletionTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#2)]  
  
4.  Добавьте закрытые поля для поставщика источника, текстовый буфер и список <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> объектов (соответствующие идентификаторы, которые будут участвовать в сеанс завершения):  
  
     [!code-csharp[VSSDKCompletionTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#3)]
     [!code-vb[VSSDKCompletionTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#3)]  
  
5.  Добавьте конструктор, который задает поставщик источника и буфера. `TestCompletionSourceProvider` Класс определен в следующих шагах:  
  
     [!code-csharp[VSSDKCompletionTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#4)]
     [!code-vb[VSSDKCompletionTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#4)]  
  
6.  Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> метод путем добавления набора завершений, который содержит завершения требуется предоставить в контексте. Каждый набор завершения содержит набор <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> завершений и соответствует вкладке окна завершения. (В проектах Visual Basic, имеют имена вкладкам окна завершения **распространенных** и **все**.) Метод FindTokenSpanAtPosition определяется на следующем шаге.  
  
     [!code-csharp[VSSDKCompletionTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#5)]
     [!code-vb[VSSDKCompletionTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#5)]  
  
7.  Следующий метод используется для поиска текущего слова начиная с позиции курсора:  
  
     [!code-csharp[VSSDKCompletionTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#6)]
     [!code-vb[VSSDKCompletionTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#6)]  
  
8.  Реализуйте `Dispose()` метод:  
  
     [!code-csharp[VSSDKCompletionTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#7)]
     [!code-vb[VSSDKCompletionTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#7)]  
  
## <a name="implementing-the-completion-source-provider"></a>Реализация поставщика источника завершения  
 Поставщик источника завершения — это часть компонентов MEF, которая создает экземпляр источника завершения.  
  
#### <a name="to-implement-the-completion-source-provider"></a>Реализация поставщика источника завершения  
  
1.  Добавьте класс с именем `TestCompletionSourceProvider` , реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>. Экспорт этого класса с <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> «текста» и <xref:Microsoft.VisualStudio.Utilities.NameAttribute> «завершения теста».  
  
     [!code-csharp[VSSDKCompletionTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#8)]
     [!code-vb[VSSDKCompletionTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#8)]  
  
2.  Импорт <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, который используется для поиска в источнике завершения текущего слова.  
  
     [!code-csharp[VSSDKCompletionTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#9)]
     [!code-vb[VSSDKCompletionTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#9)]  
  
3.  Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> метод для создания экземпляра источника завершения.  
  
     [!code-csharp[VSSDKCompletionTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletionsource.cs#10)]
     [!code-vb[VSSDKCompletionTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletionsource.vb#10)]  
  
## <a name="implementing-the-completion-command-handler-provider"></a>Реализация поставщика, обработчик завершения команды  
 Поставщиком обработчик завершения команд является производным от <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>, который прослушивает событие создания представления текста и преобразует это представление из <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>— который позволяет добавлять команды в цепочке командной оболочки Visual Studio — для <xref:Microsoft.VisualStudio.Text.Editor.ITextView>. Так как этот класс является экспорт MEF, вы также можно использовать в импорте служб, которые требуются сам обработчик команды.  
  
#### <a name="to-implement-the-completion-command-handler-provider"></a>Реализация поставщика обработчик завершения команды  
  
1.  Добавьте в файл с именем `TestCompletionCommandHandler`.  
  
2.  Добавьте следующие операторы using:  
  
     [!code-csharp[VSSDKCompletionTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#11)]
     [!code-vb[VSSDKCompletionTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#11)]  
  
3.  Добавьте класс с именем `TestCompletionHandlerProvider` , реализующий <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>. Экспорт этого класса с <xref:Microsoft.VisualStudio.Utilities.NameAttribute> «обработчика маркера завершения», <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> «текста» и <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> из <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>.  
  
     [!code-csharp[VSSDKCompletionTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#12)]
     [!code-vb[VSSDKCompletionTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#12)]  
  
4.  Импорт <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, который включает преобразование из <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> для <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>и <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> , разрешающий доступ к стандартным службам Visual Studio.  
  
     [!code-csharp[VSSDKCompletionTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#13)]
     [!code-vb[VSSDKCompletionTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#13)]  
  
5.  Реализуйте <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> метод для создания экземпляра обработчика команды.  
  
     [!code-csharp[VSSDKCompletionTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#14)]
     [!code-vb[VSSDKCompletionTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#14)]  
  
## <a name="implementing-the-completion-command-handler"></a>Реализация обработчика завершения команды  
 Поскольку завершение операторов запускается нажатиями клавиш, необходимо реализовать <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс для получения и обработки нажатий клавиш, запуска, завершения и закрыть сеанс завершения.  
  
#### <a name="to-implement-the-completion-command-handler"></a>Чтобы реализовать обработчик завершения команды  
  
1.  Добавьте класс с именем `TestCompletionCommandHandler` , реализующий <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:  
  
     [!code-csharp[VSSDKCompletionTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#15)]
     [!code-vb[VSSDKCompletionTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#15)]  
  
2.  Добавьте закрытые поля для следующий обработчик команд (к которому передать команду), представление текста, поставщиком обработчик команд (который позволяет получать доступ к различным службам) и сеанс завершения:  
  
     [!code-csharp[VSSDKCompletionTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#16)]
     [!code-vb[VSSDKCompletionTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#16)]  
  
3.  Добавьте конструктор, который задает представления текста и поля поставщика и добавляет команду в цепочку команды:  
  
     [!code-csharp[VSSDKCompletionTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#17)]
     [!code-vb[VSSDKCompletionTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#17)]  
  
4.  Реализуйте <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метод, передав команды вместе:  
  
     [!code-csharp[VSSDKCompletionTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#18)]
     [!code-vb[VSSDKCompletionTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#18)]  
  
5.  Выполните метод <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>. Когда этот метод получает нажатие клавиши, он должен выполнить одно из этих вещей:  
  
    -   Разрешить символ для записи в буфер и затем активировать или фильтрации завершения. (Печать символов для этого.)  
  
    -   Фиксировать завершение, но не разрешать символ, записываемый в буфер. (Пробелы, Tab и ввод для этого при отображении сеанс завершения.)  
  
    -   Разрешить команда передается следующий обработчик. (Все другие команды.)  
  
     Так как этот метод может отобразить пользовательский Интерфейс, вызывать <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> чтобы убедиться в том, что он не вызывается в контексте службы автоматизации:  
  
     [!code-csharp[VSSDKCompletionTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#19)]
     [!code-vb[VSSDKCompletionTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#19)]  
  
6.  Этот код — это закрытый метод, который запускает сеанс завершения:  
  
     [!code-csharp[VSSDKCompletionTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#20)]
     [!code-vb[VSSDKCompletionTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#20)]  
  
7.  В следующем примере выполняются закрытый метод, который отменяет подписку <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> событий:  
  
     [!code-csharp[VSSDKCompletionTest#21](../snippets/csharp/VS_Snippets_VSSDK/vssdkcompletiontest/cs/testcompletioncommandhandler.cs#21)]
     [!code-vb[VSSDKCompletionTest#21](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkcompletiontest/vb/testcompletioncommandhandler.vb#21)]  
  
## <a name="building-and-testing-the-code"></a>Сборка и тестирование кода  
 Чтобы протестировать этот код, выполните сборку решения CompletionTest и запустите его в экспериментальном экземпляре.  
  
#### <a name="to-build-and-test-the-completiontest-solution"></a>Построение и тестирование решения CompletionTest  
  
1.  Постройте решение.  
  
2.  При запуске этого проекта в отладчике создается второй экземпляр Visual Studio.  
  
3.  Создайте текстовый файл и введите текст, который включает слово «добавить».  
  
4.  При вводе сначала «a» и затем «d», должен отображаться список, содержащий «сложение» и «адаптации». Обратите внимание на то, что выбран сложения. При вводе другой «d», этот список должен содержать только «дополнение», который теперь можно выбрать. Можно зафиксировать «дополнение», нажав клавишу ПРОБЕЛ, Tab или ввод или закрыть список, введя Esc или любую другую клавишу.  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство. Связывание типа контента с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)


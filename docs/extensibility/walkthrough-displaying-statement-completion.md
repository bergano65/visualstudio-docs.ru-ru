---
title: "Пошаговое руководство: Отображение завершения операторов | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "редакторы [Visual Studio SDK] новый - завершение операторов"
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
caps.latest.revision: 36
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 36
---
# Пошаговое руководство: Отображение завершения операторов
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Завершение операторов на основе языка можно реализовать путем определения идентификаторов, для которых требуется предоставить завершения и затем запуск сеанса завершения. Можно определить завершение операторов в контекст языковой службы, определите расширение имени файла и тип содержимого и отображения только этот тип завершения или завершения для существующего типа содержимого можно активировать — например, «открытым текстом». В этом пошаговом руководстве показано, как вызвать завершение операторов тип содержимого «открытым текстом», который является типом содержимого текстовых файлов. Тип содержимого «text» является предком всех других типов содержимого, включая код и XML\-файлов.  
  
 Завершение операторов обычно запускается, введя некоторые символы, например, введя идентификатором, например «using» в начале. Обычно оно закрывается при нажатии клавиши ПРОБЕЛ, Tab или ввод для фиксации выделения. Можно реализовать функции IntelliSense, которые запускаются, введя символ с помощью обработчика команды клавиш \( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс\) и обработчик поставщик, реализующий <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> интерфейса. Для создания источника завершения, который является список идентификаторов, которые участвуют в завершении, реализовать <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> интерфейс и поставщик источника завершения \( <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> интерфейс\). Поставщики являются компоненты Managed Extensibility Framework \(MEF\). Они отвечают за экспортирование классов источника и контроллера и импорта служб и брокеров — например, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, позволяющий навигации в текстовом буфере и <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, триггеров сеанс завершения.  
  
 В этом пошаговом руководстве показано, как реализовать завершение операторов с жестко набор идентификаторов. В полной реализации службы языка и документации по языку несут ответственность за предоставление этого содержимого.  
  
## Обязательные компоненты  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в установку Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [Установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Создание проекта MEF  
  
#### Создание проекта MEF  
  
1.  Создайте проект VSIX C\#. \(В **Новый проект** диалогового окна выберите **Visual C\# и расширяемость**, затем **проект VSIX**.\) Присвойте решению имя `CompletionTest`.  
  
2.  Добавьте в проект шаблон элемента редактор классификатора. Дополнительные сведения см. в разделе [Создание расширения с помощью редактора шаблона элемента](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Удалите файлы существующих классов.  
  
4.  Добавьте следующие ссылки в проект и убедитесь, что **CopyLocal** задано значение `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.Shell.Immutable.10.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## Реализация источника завершения  
 Источник выполнения отвечает за сбор набор идентификаторов и добавление содержимого окна завершения, когда пользователь вводит завершения триггера, например первые буквы идентификатора. В этом примере идентификаторы и их описания жестко запрограммированы в <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> метод. В большинстве случаев реального использования используется анализатор языка для получения маркеров для заполнения списка завершения.  
  
#### Для реализации источника завершения  
  
1.  Добавьте файл класса с именем `TestCompletionSource`.  
  
2.  Добавьте эти imports:  
  
     [!code-cs[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]  
  
3.  Измените объявление класса для `TestCompletionSource` чтобы он реализовал <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>:  
  
     [!code-cs[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]  
  
4.  Добавьте закрытые поля для поставщика источника, текстовом буфере и список <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> объектов \(соответствующие идентификаторы, которые будут участвовать в сеанс завершения\):  
  
     [!code-cs[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]  
  
5.  Добавьте конструктор, который задает поставщик источника и буфера.`TestCompletionSourceProvider` Класс определяется позднее:  
  
     [!code-cs[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]  
  
6.  Реализация <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> метода, добавив завершения набор, содержащий завершения требуется предоставить в контексте. Каждый набор завершения содержит набор <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> завершений и соответствует вкладке окна завершения. \(В проектах Visual Basic с именем вкладки окна завершения **Общие** и **все**.\) Метод FindTokenSpanAtPosition определен на следующем шаге.  
  
     [!code-cs[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]  
  
7.  Следующий метод используется для поиска текущего слова в позиции курсора:  
  
     [!code-cs[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]  
  
8.  Реализация `Dispose()` метода:  
  
     [!code-cs[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]  
  
## Реализация поставщика источника завершения  
 Поставщик источника завершения — часть компонент MEF, который создает экземпляр источника завершения.  
  
#### Реализация поставщика источника завершения  
  
1.  Добавьте класс с именем `TestCompletionSourceProvider` реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>. Экспортировать класс с <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> «текста» и <xref:Microsoft.VisualStudio.Utilities.NameAttribute> «завершения тестирования».  
  
     [!code-cs[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]  
  
2.  Импорт <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, который используется для поиска текущего слова в источнике завершения.  
  
     [!code-cs[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]  
  
3.  Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> метод для создания экземпляра источника завершения.  
  
     [!code-cs[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]  
  
## Реализация поставщика обработчик завершения команды  
 Поставщик обработчик команды завершения является производным от <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>, который прослушивает события создания представления текста и преобразует представление на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>— которого позволяет добавлять команды в цепочке командной оболочке Visual Studio — для <xref:Microsoft.VisualStudio.Text.Editor.ITextView>. Поскольку этот класс является экспорт MEF, можно использовать его для служб, которые требуются сам обработчик команды импорта.  
  
#### Реализация поставщика обработчик завершения команды  
  
1.  Добавьте в файл с именем `TestCompletionCommandHandler`.  
  
2.  Добавьте следующие операторы using:  
  
     [!code-cs[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]  
  
3.  Добавьте класс с именем `TestCompletionHandlerProvider` реализующий <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>. Экспортировать класс с <xref:Microsoft.VisualStudio.Utilities.NameAttribute> «обработчика маркера завершения», <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> «текста» и <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> из <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>.  
  
     [!code-cs[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]  
  
4.  Импорт <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, который включает преобразование из <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> для <xref:Microsoft.VisualStudio.Text.Editor.ITextView>,  <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, и <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> обеспечивающий доступ к стандартной службы Visual Studio.  
  
     [!code-cs[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]  
  
5.  Реализуйте <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> метод для создания экземпляра обработчика команды.  
  
     [!code-cs[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]  
  
## Реализация обработчика команды завершения  
 Поскольку завершение операторов запускается нажатиями клавиш, необходимо реализовать <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс для получения и обработки нажатия клавиш, триггер, commit и закрыть сеанс завершения.  
  
#### Чтобы реализовать обработчик команды завершения  
  
1.  Добавьте класс с именем `TestCompletionCommandHandler` реализующий <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>:  
  
     [!code-cs[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
     [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]  
  
2.  Добавьте следующий обработчик команды \(к которому введен команды\), представления текста, поставщик обработчик команды \(который позволяет получать доступ к различным службам\), закрытые поля и завершения сеанса:  
  
     [!code-cs[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
     [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]  
  
3.  Добавьте конструктор, который задает представление текста и полей поставщика и добавляет команды цепочку команды:  
  
     [!code-cs[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
     [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]  
  
4.  Реализация <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метода путем передачи команды вместе:  
  
     [!code-cs[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
     [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]  
  
5.  Выполните метод <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>. Когда этот метод получает нажатие клавиши, он должен выполнить одно из этих действий:  
  
    -   Разрешение символов, записанных в буфер и затем триггера или отфильтровать завершения. \(Печать символов это сделать\).  
  
    -   Зафиксировать завершения, но не разрешать символ, записываемый в буфер. \(Пробелы, Tab и ввод этого при отображении сеанс завершения.\)  
  
    -   Разрешить команда передается следующий обработчик. \(Все другие команды.\)  
  
     Поскольку этот метод может отображать пользовательский Интерфейс, вызовите <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> Чтобы убедиться в том, что он не вызывается в контексте автоматизации:  
  
     [!code-cs[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]  
  
6.  Данный пример кода является закрытый метод, который инициирует сеанс завершения:  
  
     [!code-cs[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
     [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]  
  
7.  В следующем примере выполняются закрытый метод, который отменяет подписку на <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> событий:  
  
     [!code-cs[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
     [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]  
  
## Сборка и тестирование кода  
 Чтобы проверить код, создания CompletionTest решения и запустите его в экспериментальном экземпляре.  
  
#### Для построения и тестирования решений CompletionTest  
  
1.  Постройте решение.  
  
2.  При запуске этого проекта в отладчике создается второй экземпляр Visual Studio.  
  
3.  Создайте текстовый файл и введите текст, который включает слово «добавить».  
  
4.  При вводе первых «a» и затем «d», появится список, содержащий «сложение» и «адаптации». Обратите внимание, что выбран сложения. При вводе другой «d», список должен содержать только «сложение», что будет выделена. Можно зафиксировать «сложение», нажав клавишу ПРОБЕЛ, Tab или ввод или закрыть список, нажав клавишу Esc или любую другую клавишу.  
  
## См. также  
 [Пошаговое руководство: Связывание типа контента с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
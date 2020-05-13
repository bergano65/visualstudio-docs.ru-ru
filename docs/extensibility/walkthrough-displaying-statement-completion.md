---
title: 'Пошаговая прогулка: Отображение завершения заявления (ru) Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - statement completion
ms.assetid: f3152c4e-7673-4047-a079-2326941d1c83
author: acangialosi
ms.author: anthc
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: 1d2f5499511c9dc0bbb6711d0da630315384f8e7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697413"
---
# <a name="walkthrough-display-statement-completion"></a>Пошаговое руководство. Отображение завершения операторов
Вы можете реализовать завершение оператора на основе языка, определив идентификаторы, для которых требуется завершить, а затем инициируя сеанс завершения. Вы можете определить завершение оператора в контексте языковой службы, определить свое расширение и тип содержимого имени файла, а затем отобразить завершение именно для этого типа. Или можно инициировать завершение для существующего типа содержимого, например, "plaintext". В этом пошаговом показании, как инициировать завершение выполнения оператора для типа содержимого "plaintext", который является типом содержимого текстовых файлов. Тип содержимого "текст" является предком всех других типов контента, включая код и XML-файлы.

 Завершение оператора обычно приводит к вводе определенных символов, например, путем ввода начала идентификатора, например ,использование». Это, как правило, уволены, нажав **Spacebar**, **Tab**, или **Введите** ключ, чтобы совершить выбор. Функции IntelliSense можно реализовать при вводе персонажа, используя обработчик команды <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> для нажатий клавиш (интерфейс) <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> и поставщика обработчиков, который реализует интерфейс. Чтобы создать источник завершения, который представляет собой список идентификаторов, участвующих в завершении, реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> интерфейс и поставщика источника завершения <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider> (интерфейс). Поставщики являются компонентами управляемой расширительности (MEF). Они отвечают за экспорт классов исходного кода и контроллера, а <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>также за импорт услуг и брокеров, например, навигацию в буфере текста, и <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>, которая запускает сеанс завершения.

 В этом пошаговом показании, как реализовать завершение оператора для жестко закодированного набора идентификаторов. В полной реализации, языковая служба и языковая документация несут ответственность за предоставление этого содержания.

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, вы не устанавливаете Visual Studio SDK из центра загрузки. Он включен в качестве дополнительной функции в Visual Studio установки. Вы также можете установить VS SDK позже. Для получения дополнительной информации, [см.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-mef-project"></a>Создание проекта MEF

#### <a name="to-create-a-mef-project"></a>Создание проекта MEF

1. Создайте проект СЗ VSIX. (В **диалоге нового проекта** выберите **Visual C / Расширяемость,** затем **VSIX Project**.) Назовите решение. `CompletionTest`

2. Добавьте шаблон элемента классификатора редактора в проект. Для получения дополнительной информации [см. Создать расширение с шаблоном элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Удалите файлы существующих классов.

4. Добавьте следующие ссылки на проект и убедитесь, что **CopyLocal** настроен на: `false`

     Microsoft.VisualStudio.Редактор

     Microsoft.VisualStudio.Language.Intellisense

     Microsoft.VisualStudio.OLE.Interop

     Microsoft.VisualStudio.Shell.15.0

     Microsoft.VisualStudio.Shell.Immutable.10.0

     Microsoft.VisualStudio.TextManager.Interop

## <a name="implement-the-completion-source"></a>Реализация источника завершения
 Источник завершения отвечает за сбор набора идентификаторов и добавление содержимого в окно завершения, когда пользователь вводит триггер завершения, например первые буквы идентификатора. В этом примере идентификаторы и их <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> описания жестко закодированы в методе. В большинстве реальных применений, вы будете использовать парзер вашего языка, чтобы получить маркеры для заполнения списка завершения.

### <a name="to-implement-the-completion-source"></a>Для реализации источника завершения

1. Добавьте файл класса с именем `TestCompletionSource`.

2. Добавьте эти импорты:

     [!code-csharp[VSSDKCompletionTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_1.cs)]
     [!code-vb[VSSDKCompletionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_1.vb)]

3. Измените декларацию `TestCompletionSource` класса так, <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>чтобы она реализовывала:

     [!code-csharp[VSSDKCompletionTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_2.cs)]
     [!code-vb[VSSDKCompletionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_2.vb)]

4. Добавьте частные поля для поставщика исходных данных, текстовый буфер и список объектов <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> (которые соответствуют идентификаторам, которые будут участвовать в сеансе завершения):

     [!code-csharp[VSSDKCompletionTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_3.cs)]
     [!code-vb[VSSDKCompletionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_3.vb)]

5. Добавьте конструктор, который устанавливает поставщик исходного кода и буфер. Класс `TestCompletionSourceProvider` определяется в более поздних шагах:

     [!code-csharp[VSSDKCompletionTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_4.cs)]
     [!code-vb[VSSDKCompletionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_4.vb)]

6. Реализуем <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource.AugmentCompletionSession%2A> метод, добавляя набор завершения, содержащий завершения, которые вы хотите предоставить в контексте. Каждый набор завершения <xref:Microsoft.VisualStudio.Language.Intellisense.Completion> содержит набор завершений и соответствует вкладке окна завершения. (В визуальных основных проектах вкладки окна завершения называются **общими** и **всеми**.) Метод `FindTokenSpanAtPosition` определяется на следующем этапе.

     [!code-csharp[VSSDKCompletionTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_5.cs)]
     [!code-vb[VSSDKCompletionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_5.vb)]

7. Для поиска текущего слова из положения курсора используется следующий метод:

     [!code-csharp[VSSDKCompletionTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_6.cs)]
     [!code-vb[VSSDKCompletionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_6.vb)]

8. Реализация `Dispose()` метода:

     [!code-csharp[VSSDKCompletionTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_7.cs)]
     [!code-vb[VSSDKCompletionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_7.vb)]

## <a name="implement-the-completion-source-provider"></a>Реализация поставщика источника завершения
 Поставщиком источника завершения является компонент MEF, который мгновенно вызывает источник завершения.

### <a name="to-implement-the-completion-source-provider"></a>Для реализации поставщика источника завершения

1. Добавьте класс, названный, `TestCompletionSourceProvider` который <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider>реализуется. Экспортировать этот <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> класс с "plaintext" и <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "тест завершения".

     [!code-csharp[VSSDKCompletionTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_8.cs)]
     [!code-vb[VSSDKCompletionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_8.vb)]

2. Импорт <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, который находит текущее слово в источнике завершения.

     [!code-csharp[VSSDKCompletionTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_9.cs)]
     [!code-vb[VSSDKCompletionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_9.vb)]

3. Реализация <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSourceProvider.TryCreateCompletionSource%2A> метода для мгновенного получения источника завершения.

     [!code-csharp[VSSDKCompletionTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_10.cs)]
     [!code-vb[VSSDKCompletionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_10.vb)]

## <a name="implement-the-completion-command-handler-provider"></a>Реализация поставщика обработок обработчика команд завершения
 Поставщик обработчика команд завершения <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>происходит от , который слушает событие создания текстового представления и преобразует представление из <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>— что позволяет добавить <xref:Microsoft.VisualStudio.Text.Editor.ITextView>команду к командной цепочке оболочки Visual Studio — в . Поскольку этот класс является экспортом MEF, его можно использовать для импорта служб, необходимых самому обработчику команд.

#### <a name="to-implement-the-completion-command-handler-provider"></a>Реализация поставщика обработок обработчика команд завершения

1. Добавить файл `TestCompletionCommandHandler`с именем .

2. Добавьте их с помощью директив:

     [!code-csharp[VSSDKCompletionTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_11.cs)]
     [!code-vb[VSSDKCompletionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_11.vb)]

3. Добавьте класс, названный, `TestCompletionHandlerProvider` который <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener>реализуется. Экспортировать этот <xref:Microsoft.VisualStudio.Utilities.NameAttribute> класс с "обработчиком <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> завершения токенов", <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> <xref:Microsoft.VisualStudio.Text.Editor.PredefinedTextViewRoles.Editable>"plaintext" и a .

     [!code-csharp[VSSDKCompletionTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_12.cs)]
     [!code-vb[VSSDKCompletionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_12.vb)]

4. Импорт <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>, который позволяет <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> конверсии из a <xref:Microsoft.VisualStudio.Text.Editor.ITextView>в , а, <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>и что <xref:Microsoft.VisualStudio.Shell.SVsServiceProvider> позволяет получить доступ к стандартным услугам Visual Studio.

     [!code-csharp[VSSDKCompletionTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_13.cs)]
     [!code-vb[VSSDKCompletionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_13.vb)]

5. Реализация <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> метода мгновенного обработчика команд.

     [!code-csharp[VSSDKCompletionTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_14.cs)]
     [!code-vb[VSSDKCompletionTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_14.vb)]

## <a name="implement-the-completion-command-handler"></a>Реализация обработчика команды завершения
 Поскольку завершение выполнения оператора запускается нажатиями клавиш, необходимо реализовать <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс для получения и обработки нажатий клавиш, которые запускают, фиксировать и увольнять сеанс завершения.

#### <a name="to-implement-the-completion-command-handler"></a>Реализация обработчика команды завершения

1. Добавить класс `TestCompletionCommandHandler` с <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>именем, который реализует:

    [!code-csharp[VSSDKCompletionTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_15.cs)]
    [!code-vb[VSSDKCompletionTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_15.vb)]

2. Добавьте частные поля для следующего обработчика команд (к которому вы передаете команду), текстовое представление, поставщик обработчиков команд (который позволяет получить доступ к различным службам) и сеанс завершения:

    [!code-csharp[VSSDKCompletionTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_16.cs)]
    [!code-vb[VSSDKCompletionTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_16.vb)]

3. Добавьте конструктор, который устанавливает представление текста и поля поставщика и добавляет команду в цепочку команд:

    [!code-csharp[VSSDKCompletionTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_17.cs)]
    [!code-vb[VSSDKCompletionTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_17.vb)]

4. Реализация <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метода, передавая команду вместе:

    [!code-csharp[VSSDKCompletionTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_18.cs)]
    [!code-vb[VSSDKCompletionTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_18.vb)]

5. Выполните метод <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A>. Когда этот метод получает нажатие клавиши, он должен сделать одну из этих вещей:

   - Разрешить символ, который будет записан в буфер, а затем вызвать или фильтр завершения. (Печать символов делает это.)

   - Совершите завершение, но не позволяйте символу быть записанным в буфер. (Whitespace, **Tab**, и **Введите** сделать это, когда сеанс завершения отображается.)

   - Разрешить передаваемую команду следующему обработчику. (Все остальные команды.)

     Поскольку этот метод может <xref:Microsoft.VisualStudio.Shell.VsShellUtilities.IsInAutomationFunction%2A> отображать uI, позвоните, чтобы убедиться, что он не называется в контексте автоматизации:

     [!code-csharp[VSSDKCompletionTest#19](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_19.cs)]
     [!code-vb[VSSDKCompletionTest#19](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_19.vb)]

6. Этот код является закрытым методом, который запускает сеанс завершения:

    [!code-csharp[VSSDKCompletionTest#20](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_20.cs)]
    [!code-vb[VSSDKCompletionTest#20](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_20.vb)]

7. Следующим примером является частный метод, <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseSession.Dismissed> который отписывается от события:

    [!code-csharp[VSSDKCompletionTest#21](../extensibility/codesnippet/CSharp/walkthrough-displaying-statement-completion_21.cs)]
    [!code-vb[VSSDKCompletionTest#21](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-statement-completion_21.vb)]

## <a name="build-and-test-the-code"></a>Создание и тестирование кода
 Чтобы протестировать этот код, создайте решение CompletionTest и запустите его в экспериментальном экземпляре.

#### <a name="to-build-and-test-the-completiontest-solution"></a>Создание и тестирование решения CompletionTest

1. Создайте решение.

2. При запуске этого проекта в отладчике запускается второй экземпляр Visual Studio.

3. Создайте текстовый файл и введите текст, который включает в себя слово "добавить".

4. При вводе сначала "a", а затем "d", должен появиться список, содержащий "дополнение" и "адаптация". Обратите внимание, что выбрано дополнение. При вводе другого "d", список должен содержать только "дополнение", которое теперь выбрано. Вы можете совершить "дополнение", нажав **Spacebar**, **Tab**, или **Введите** ключ, или уволить список, введя Esc или любой другой ключ.

## <a name="see-also"></a>См. также
- [Прохождение: Свяжите тип содержимого с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)

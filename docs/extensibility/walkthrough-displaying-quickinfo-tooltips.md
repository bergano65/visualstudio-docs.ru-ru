---
title: 'Пошаговая прогулка: Отображение быстрых Info Tooltips (ru) Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- csharp
- vb
ms.openlocfilehash: 47a14ca0692ad0338b56fd1d372307fb0e2ccc4c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697437"
---
# <a name="walkthrough-display-quickinfo-tooltips"></a>Прохождение: Отображение инструментов quickInfo
КвикИнфо — это функция IntelliSense, которая отображает подписи и описания метода, когда пользователь перемещает указатель по имени метода. Можно реализовать функции, основанные на языке, такие как квикинфофо, определив идентификаторы, для которых вы хотите предоставить описания quickInfo, а затем создав набор инструментов, в котором можно отобразить содержимое. Вы можете определить квикИнфо в контексте языковой службы, или вы можете определить свое собственное расширение имени файла и тип содержимого и отобразить квикИнфо для именно этого типа, или вы можете отобразить квикИнфо для существующего типа содержимого (например, "текст"). В этом пошаговом показании, как отобразить «текст» типа содержимого.

 Пример «КвикИнфо» в этом пошаговом шаге отображает наконечники инструментов, когда пользователь перемещает указатель по имени метода. Эта конструкция требует, чтобы вы реализовали эти четыре интерфейса:

- исходный интерфейс

- интерфейс поставщика исходного кода

- интерфейс контроллера

- интерфейс контроллера поставщика

  Поставщики источников и контроллеров являются компонентными компонентами Управляемой расширительности (MEF) и отвечают за экспорт <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>классов исходного кода и контроллера, а также за импорт услуг и брокеров, таких как , который создает буфер текста tooltip, и <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>, который запускает сеанс quickInfo.

  В этом примере источник «КвикИнфо» использует жесткий список имен и описаний методов, но в полной мере за предоставление этого содержимого отвечает языковая служба и языковая документация.

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, вам не нужно устанавливать Visual Studio SDK из центра загрузки. Он включен в качестве дополнительной функции в Visual Studio установки. Вы также можете установить VS SDK позже. Для получения дополнительной информации, [см.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-mef-project"></a>Создание проекта MEF

### <a name="to-create-a-mef-project"></a>Создание проекта MEF

1. Создайте проект СЗ VSIX. (В **диалоге нового проекта** выберите **Visual C / Расширяемость,** затем **VSIX Project**.) Назовите решение. `QuickInfoTest`

2. Добавьте шаблон элемента классификатора редактора в проект. Для получения дополнительной информации [см. Создать расширение с шаблоном элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Удалите файлы существующих классов.

## <a name="implement-the-quickinfo-source"></a>Реализация источника «БыстрыйИнфо»
 Источник «КвикИнфо» отвечает за сбор набора идентификаторов и их описания и добавление содержимого в буфер текста инструментария при обнаружении одного из идентификаторов. В этом примере идентификаторы и их описания просто добавляются в конструктор источника.

#### <a name="to-implement-the-quickinfo-source"></a>Для реализации источника «БыстрыйИнфо»

1. Добавьте файл класса с именем `TestQuickInfoSource`.

2. Добавить ссылку на *Microsoft.VisualStudio.Language.IntelliSense*.

3. Добавьте приведенные ниже импортированные данные.

     [!code-vb[VSSDKQuickInfoTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_1.vb)]
     [!code-csharp[VSSDKQuickInfoTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_1.cs)]

4. Объявить класс, <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>который реализует, `TestQuickInfoSource`и назвать его.

     [!code-vb[VSSDKQuickInfoTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_2.vb)]
     [!code-csharp[VSSDKQuickInfoTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_2.cs)]

5. Добавьте поля для поставщика источников быстрого инфо, текстовый буфер и набор имен и подписей метода. В этом примере имена и подписи `TestQuickInfoSource` метода инициализируются в конструкторе.

     [!code-vb[VSSDKQuickInfoTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_3.vb)]
     [!code-csharp[VSSDKQuickInfoTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_3.cs)]

6. Добавьте конструктор, который устанавливает поставщик источников быстрого кода и текстовый буфер и заполняет набор имен методов, а также подписи и описания методов.

     [!code-vb[VSSDKQuickInfoTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_4.vb)]
     [!code-csharp[VSSDKQuickInfoTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_4.cs)]

7. Выполните метод <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A>. В этом примере метод находит текущее слово или предыдущее слово, если курсор находится в конце строки или буфера текста. Если слово является одним из имен метода, описание имени этого метода добавляется в содержимое quickInfo.

     [!code-vb[VSSDKQuickInfoTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_5.vb)]
     [!code-csharp[VSSDKQuickInfoTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_5.cs)]

8. Необходимо также реализовать метод Dispose() <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> с <xref:System.IDisposable>момента реализации:

     [!code-vb[VSSDKQuickInfoTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_6.vb)]
     [!code-csharp[VSSDKQuickInfoTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_6.cs)]

## <a name="implement-a-quickinfo-source-provider"></a>Реализация поставщика источников быстрого инфосида
 Поставщик источника «КвикИнфо» служит в первую очередь для экспорта в качестве компонентной части MEF и мгновенно ускоряет источник «КвикИнфо». Поскольку это компонент MEF, он может импортировать другие компоненты MEF.

#### <a name="to-implement-a-quickinfo-source-provider"></a>Для реализации поставщика источников быстрого инфосимы

1. Объявить источник поставщика `TestQuickInfoSourceProvider` квикинфо, названный, который <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>реализует, и экспортировать его с <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "ToolTip Быстрый Источник", <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> до "по умолчанию", и <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "текст".

     [!code-vb[VSSDKQuickInfoTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_7.vb)]
     [!code-csharp[VSSDKQuickInfoTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_7.cs)]

2. Импортируйте два <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> сервиса <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>редактора, `TestQuickInfoSourceProvider`и, как свойства .

     [!code-vb[VSSDKQuickInfoTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_8.vb)]
     [!code-csharp[VSSDKQuickInfoTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_8.cs)]

3. Реализация <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> для возврата `TestQuickInfoSource`нового .

     [!code-vb[VSSDKQuickInfoTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_9.vb)]
     [!code-csharp[VSSDKQuickInfoTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_9.cs)]

## <a name="implement-a-quickinfo-controller"></a>Реализация контроллера квикИнфо
 Контроллеры quickInfo определяют, когда отображается quickInfo. В этом примере отослана киктфофозанджера, когда указатель находится над словом, которое соответствует одному из имен метода. Контроллер «КвикИнфо» реализует обработчик событий, нависший над мышью, который запускает сеанс «КвикИнфо».

### <a name="to-implement-a-quickinfo-controller"></a>Для реализации контроллера quickInfo

1. Объявить класс, <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>который реализует, `TestQuickInfoController`и назвать его.

     [!code-vb[VSSDKQuickInfoTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_10.vb)]
     [!code-csharp[VSSDKQuickInfoTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_10.cs)]

2. Добавьте частные поля для представления текста, текстовые буферы, представленные в текстовом представлении, сеанса квикинфо и поставщика контроллеров quickInfo.

     [!code-vb[VSSDKQuickInfoTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_11.vb)]
     [!code-csharp[VSSDKQuickInfoTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_11.cs)]

3. Добавьте конструктор, который устанавливает поля и добавляет обработчик событий мыши.

     [!code-vb[VSSDKQuickInfoTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_12.vb)]
     [!code-csharp[VSSDKQuickInfoTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_12.cs)]

4. Добавьте обработчик события нависшей на мышах, который запускает сеанс «КвикИнфо».

     [!code-vb[VSSDKQuickInfoTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_13.vb)]
     [!code-csharp[VSSDKQuickInfoTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_13.cs)]

5. Реализация <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> метода так, чтобы он удалял обработчик события мыши, когда контроллер отделился от представления текста.

     [!code-vb[VSSDKQuickInfoTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_14.vb)]
     [!code-csharp[VSSDKQuickInfoTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_14.cs)]

6. <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> Внедрить <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> метод и метод в виде пустых методов для этого примера.

     [!code-vb[VSSDKQuickInfoTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_15.vb)]
     [!code-csharp[VSSDKQuickInfoTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_15.cs)]

## <a name="implementing-the-quickinfo-controller-provider"></a>Внедрение поставщика контроллеров квикИнФО
 Поставщик контроллера quickInfo служит в первую очередь для экспорта себя в качестве компонента MEF часть и мгновенно контроллера quickInfo. Поскольку это компонент MEF, он может импортировать другие компоненты MEF.

### <a name="to-implement-the-quickinfo-controller-provider"></a>Для реализации поставщика контроллеров квикИнфо

1. `TestQuickInfoControllerProvider` Объявить класс, названный, который <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>реализует, и экспортировать его с <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "ToolTip контроллер амподром" и "текст":

     [!code-vb[VSSDKQuickInfoTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_16.vb)]
     [!code-csharp[VSSDKQuickInfoTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_16.cs)]

2. Импортируйте <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> как свойство.

     [!code-vb[VSSDKQuickInfoTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_17.vb)]
     [!code-csharp[VSSDKQuickInfoTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_17.cs)]

3. Реализация <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> метода путем мгновенного контроллера quickInfo.

     [!code-vb[VSSDKQuickInfoTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_18.vb)]
     [!code-csharp[VSSDKQuickInfoTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_18.cs)]

## <a name="build-and-test-the-code"></a>Создайте и протестуйте Код
 Чтобы протестировать этот код, создайте решение для быстрого Инфотеста и запустите его в экспериментальном экземпляре.

### <a name="to-build-and-test-the-quickinfotest-solution"></a>Для создания и тестирования решения для быстрого Инфотеста

1. Создайте решение.

2. При запуске этого проекта в отладчике запускается второй экземпляр Visual Studio.

3. Создайте текстовый файл и введите текст, который включает в себя слова "добавить" и "вычесть".

4. Переместите указатель на один из случаев "добавить". Подпись и описание метода `add` должны отображаться.

## <a name="see-also"></a>См. также
- [Прохождение: Свяжите тип содержимого с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)

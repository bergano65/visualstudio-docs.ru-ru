---
title: Пошаговое руководство. Отображение всплывающих подсказок для кратких сведений | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - QuickInfo
ms.assetid: 23fb8384-4f12-446f-977f-ce7910347947
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b7cb51edb41109d9664e5aeda0a5393d2cd34f38
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66312435"
---
# <a name="walkthrough-display-quickinfo-tooltips"></a>Пошаговое руководство. Отображение всплывающих подсказок для кратких сведений
Кратких сведений является функцией IntelliSense, отображающий сигнатуры методов и описания, когда пользователь перемещает указатель на имя метода. Характеристики на основе языка, например кратких сведений можно реализовать путем определения идентификаторов, для которых вы хотите предоставить описания кратких сведений, а также Создание всплывающей подсказки, в которой для отображения содержимого. Кратких сведений можно определить в контексте службы языка, можно определить тип имени собственного файла расширения и содержимого и отображения кратких сведений для только этого типа или можно отобразить кратких сведений для существующих типов (например, «text»). В этом пошаговом руководстве показано, как для отображения кратких сведений для типа содержимого «text».

 В примере кратких сведений в этом пошаговом руководстве отображает всплывающие подсказки при наведении указателя мыши на имени метода. Такой подход требует реализации этих четырех интерфейсов:

- исходный интерфейс

- интерфейс поставщика источника

- интерфейс контроллера

- интерфейс поставщика контроллера

  Поставщики источника и контроллера, компоненты Managed Extensibility Framework (MEF) и несут ответственность за экспортирование классов источника и контроллера и импорт служб и брокеры, такие как <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, который создает текст всплывающей подсказки буфер и <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker>, который запускает сеанс кратких сведений.

  В этом примере источник кратких сведений использует жестко список имен методов и описаний, но в полной реализации языковой службы и документацию по языку несут ответственность за предоставление этого содержимого.

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, не нужно установить пакет SDK для Visual Studio из центра загрузки. Этот пакет включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установить пакет SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Создание проекта MEF

### <a name="to-create-a-mef-project"></a>Создание проекта MEF

1. Создайте проект VSIX C#. (В **новый проект** диалоговом окне выберите **Visual C# / Extensibility**, затем **проект VSIX**.) Назовите решение `QuickInfoTest`.

2. Добавьте в проект шаблон элемента классификатора редактора. Дополнительные сведения см. в разделе [создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Удалите файлы существующих классов.

## <a name="implement-the-quickinfo-source"></a>Реализуйте источник кратких сведений
 Источник кратких сведений отвечает за сбор набор идентификаторов и их описания и при обнаружении один из идентификаторов, добавление содержимого в буфер текста всплывающей подсказки. В этом примере идентификаторы и их описания только что добавили в конструкторе источника.

#### <a name="to-implement-the-quickinfo-source"></a>Для реализации источник кратких сведений

1. Добавьте файл класса с именем `TestQuickInfoSource`.

2. Добавьте ссылку на *Microsoft.VisualStudio.Language.IntelliSense*.

3. Добавьте следующие импорты.

     [!code-vb[VSSDKQuickInfoTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_1.vb)]
     [!code-csharp[VSSDKQuickInfoTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_1.cs)]

4. Объявите класс, реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource>и назовите его `TestQuickInfoSource`.

     [!code-vb[VSSDKQuickInfoTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_2.vb)]
     [!code-csharp[VSSDKQuickInfoTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_2.cs)]

5. Добавьте поля для поставщика источника кратких сведений, текстового буфера и набор имен методов и подписи методов. В этом примере имена и подписи методов инициализируются в `TestQuickInfoSource` конструктор.

     [!code-vb[VSSDKQuickInfoTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_3.vb)]
     [!code-csharp[VSSDKQuickInfoTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_3.cs)]

6. Добавьте конструктор, который задает поставщик источника кратких сведений и текстовый буфер и заполняет набор имен методов и подписи методов и описания.

     [!code-vb[VSSDKQuickInfoTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_4.vb)]
     [!code-csharp[VSSDKQuickInfoTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_4.cs)]

7. Выполните метод <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource.AugmentQuickInfoSession%2A>. В этом примере метод находит текущего слова или предыдущего слова, если курсор находится в конце строки или буфера текста. Если слово является одним из имен методов, описание для этого имени метода добавляется к содержимому кратких сведений.

     [!code-vb[VSSDKQuickInfoTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_5.vb)]
     [!code-csharp[VSSDKQuickInfoTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_5.cs)]

8. Необходимо также реализовать метод Dispose(), поскольку <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSource> реализует <xref:System.IDisposable>:

     [!code-vb[VSSDKQuickInfoTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_6.vb)]
     [!code-csharp[VSSDKQuickInfoTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_6.cs)]

## <a name="implement-a-quickinfo-source-provider"></a>Реализация поставщика источника кратких сведений
 Поставщик источника кратких сведений служит главным образом для экспортировать сама себя в качестве компонента MEF и создание экземпляра источник кратких сведений. Так как он является частью компонента MEF, его можно импортировать другие компоненты MEF.

#### <a name="to-implement-a-quickinfo-source-provider"></a>Для реализации поставщика источника кратких сведений

1. Объявите версиями кратких сведений с именем `TestQuickInfoSourceProvider` , реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider>и экспортировать его с <xref:Microsoft.VisualStudio.Utilities.NameAttribute> «Подсказки источника кратких сведений,» <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> из Before = «default» и <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> «текст».

     [!code-vb[VSSDKQuickInfoTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_7.vb)]
     [!code-csharp[VSSDKQuickInfoTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_7.cs)]

2. Импорт две службы редактора, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> и <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService>, как свойства `TestQuickInfoSourceProvider`.

     [!code-vb[VSSDKQuickInfoTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_8.vb)]
     [!code-csharp[VSSDKQuickInfoTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_8.cs)]

3. Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoSourceProvider.TryCreateQuickInfoSource%2A> возвращается новый `TestQuickInfoSource`.

     [!code-vb[VSSDKQuickInfoTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_9.vb)]
     [!code-csharp[VSSDKQuickInfoTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_9.cs)]

## <a name="implement-a-quickinfo-controller"></a>Реализация контроллера кратких сведений
 Контроллеры кратких сведений определяют, когда отображается кратких сведений. В этом примере кратких сведений отображается, когда указатель находится над слово, которое соответствует одному из имен методов. Контроллер кратких сведений реализует обработчик событий мыши при наведении указателя мыши, которое запускает сеанс кратких сведений.

### <a name="to-implement-a-quickinfo-controller"></a>Для реализации контроллера кратких сведений

1. Объявите класс, реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController>и назовите его `TestQuickInfoController`.

     [!code-vb[VSSDKQuickInfoTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_10.vb)]
     [!code-csharp[VSSDKQuickInfoTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_10.cs)]

2. Добавьте закрытые поля для представления текста, текстовых буферов, представленных в представление текста, сеанс кратких сведений и поставщиком контроллера кратких сведений.

     [!code-vb[VSSDKQuickInfoTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_11.vb)]
     [!code-csharp[VSSDKQuickInfoTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_11.cs)]

3. Добавьте конструктор, который задает поля и добавляет обработчик событий при наведении мыши.

     [!code-vb[VSSDKQuickInfoTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_12.vb)]
     [!code-csharp[VSSDKQuickInfoTest#12](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_12.cs)]

4. Добавьте обработчик событий мыши при наведении указателя мыши, которое запускает сеанс кратких сведений.

     [!code-vb[VSSDKQuickInfoTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_13.vb)]
     [!code-csharp[VSSDKQuickInfoTest#13](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_13.cs)]

5. Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.Detach%2A> метода, так что он удаляет обработчик событий при наведении указателя мыши, если контроллер отсоединяется от представления текста.

     [!code-vb[VSSDKQuickInfoTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_14.vb)]
     [!code-csharp[VSSDKQuickInfoTest#14](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_14.cs)]

6. Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.ConnectSubjectBuffer%2A> метод и <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseController.DisconnectSubjectBuffer%2A> метод как пустых методов в этом примере.

     [!code-vb[VSSDKQuickInfoTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_15.vb)]
     [!code-csharp[VSSDKQuickInfoTest#15](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_15.cs)]

## <a name="implementing-the-quickinfo-controller-provider"></a>Реализация поставщика контроллера кратких сведений
 Поставщик кратких сведений контроллера служит главным образом для экспортировать сама себя в качестве компонента MEF и создание экземпляра контроллера кратких сведений. Так как он является частью компонента MEF, его можно импортировать другие компоненты MEF.

### <a name="to-implement-the-quickinfo-controller-provider"></a>Реализация поставщика контроллера кратких сведений

1. Объявите класс с именем `TestQuickInfoControllerProvider` , реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider>и экспортировать его с <xref:Microsoft.VisualStudio.Utilities.NameAttribute> «Контроллера кратких сведений, подсказка» и <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> «текст»:

     [!code-vb[VSSDKQuickInfoTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_16.vb)]
     [!code-csharp[VSSDKQuickInfoTest#16](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_16.cs)]

2. Импортируйте <xref:Microsoft.VisualStudio.Language.Intellisense.IQuickInfoBroker> как свойство.

     [!code-vb[VSSDKQuickInfoTest#17](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_17.vb)]
     [!code-csharp[VSSDKQuickInfoTest#17](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_17.cs)]

3. Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.IIntellisenseControllerProvider.TryCreateIntellisenseController%2A> метод путем создания экземпляра контроллера кратких сведений.

     [!code-vb[VSSDKQuickInfoTest#18](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-quickinfo-tooltips_18.vb)]
     [!code-csharp[VSSDKQuickInfoTest#18](../extensibility/codesnippet/CSharp/walkthrough-displaying-quickinfo-tooltips_18.cs)]

## <a name="build-and-test-the-code"></a>Построение и тестирование кода
 Чтобы протестировать этот код, выполните сборку решения QuickInfoTest и запустите его в экспериментальном экземпляре.

### <a name="to-build-and-test-the-quickinfotest-solution"></a>Построение и тестирование решения QuickInfoTest

1. Постройте решение.

2. При запуске этого проекта в отладчике, запускается второй экземпляр Visual Studio.

3. Создайте текстовый файл и введите текст, который содержит слова «добавить» и «вычитание».

4. Наведите указатель на одно из вхождений «добавить». Подпись и описание `add` метод должны отображаться.

## <a name="see-also"></a>См. также
- [Пошаговое руководство: Связывание типа контента с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
---
title: "Пошаговое руководство: Отображение справки сигнатуры | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "редакторы [Visual Studio SDK] новый - подпись справки и сведения о параметрах"
ms.assetid: 4a6a884b-5730-4b54-9264-99684f5b523c
caps.latest.revision: 28
caps.handback.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
---
# Пошаговое руководство: Отображение справки сигнатуры
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Справка сигнатуры \(также известный как *сведения о параметрах*\) отображает сигнатура метода во всплывающей подсказке, когда пользователь вводит знак начала списка параметров \(обычно открывающая скобка\). Как параметр и параметр разделителем \(обычно запятой\) типизированы, подсказка обновляется для отображения следующего параметра полужирным шрифтом. Справка по сигнатурам можно определить в контекст языковой службы, можно определить собственный файл имя расширения или типу содержимого и отобразить справку по подписи для только этот тип или можно отобразить справку по подписи для существующего типа контента \(например, «текст»\). В этом пошаговом руководстве показано, как отобразить справку по подписи для типа содержимого «text».  
  
 Справка сигнатуры обычно запускается, введя определенный символ, например, «\(«\(открывающая скобка\) и закрытия, введя другой символ, например, «\)» \(закрывающая круглая скобка\). Функции IntelliSense, которые запускаются, введя символ может быть реализован с помощью обработчика команды клавиш \( <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс\) и обработчик поставщик, реализующий <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> интерфейса. Для создания источника справка сигнатуры, которым список подписей, участвующих в справке подпись, реализовать <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource> интерфейс и поставщик источника, который реализует <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider> интерфейса. Поставщиков компонентов Managed Extensibility Framework \(MEF\) и ответственны за экспортирование классов источника и контроллера и импорта служб и брокеров, например, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService>, позволяет перейти в текстовом буфере и <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker>, который запускает сеанс справки сигнатуры.  
  
 В этом пошаговом руководстве демонстрируется реализация справки сигнатуры для жестко набор идентификаторов. В полной реализации языка отвечает за предоставление этого содержимого.  
  
## Обязательные компоненты  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в установку Visual Studio. VS SDK также можно установить позже. Для получения дополнительной информации см. [Установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Создание проекта MEF  
  
#### Создание проекта MEF  
  
1.  Создайте проект VSIX C\#. \(В **Новый проект** диалогового окна выберите **Visual C\# и расширяемость**, затем **проект VSIX**.\) Присвойте решению имя `SignatureHelpTest`.  
  
2.  Добавьте в проект шаблон элемента редактор классификатора. Для получения дополнительной информации см. [Создание расширения с помощью редактора шаблона элемента](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Удалите файлы существующих классов.  
  
4.  Добавьте следующие ссылки в проект и убедитесь, что **CopyLocal** задано значение `false`:  
  
     Microsoft.VisualStudio.Editor  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
     Microsoft.VisualStudio.OLE.Interop  
  
     Microsoft.VisualStudio.Shell.14.0  
  
     Microsoft.VisualStudio.TextManager.Interop  
  
## Реализация подпись справка сигнатуры и параметры  
 Источник справки сигнатуры основывается на подписей, которые реализуют <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>, каждый из которых содержит параметры, которые реализуют <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>. В полной реализации эти сведения будут получены из документации по языку, но в этом примере подписи жестко запрограммированы.  
  
#### Для реализации подпись справка сигнатуры и параметры  
  
1.  Добавьте файл класса с именем `SignatureHelpSource`.  
  
2.  Добавьте следующие операторы imports.  
  
     [!CODE [VSSDKSignatureHelpTest#1](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#1)]  
  
3.  Добавьте класс с именем `TestParameter` реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!CODE [VSSDKSignatureHelpTest#2](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#2)]  
  
4.  Добавьте конструктор, который задает всем свойствам.  
  
     [!CODE [VSSDKSignatureHelpTest#3](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#3)]  
  
5.  Добавление свойства <xref:Microsoft.VisualStudio.Language.Intellisense.IParameter>.  
  
     [!CODE [VSSDKSignatureHelpTest#4](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#4)]  
  
6.  Добавьте класс с именем `TestSignature` реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature>.  
  
     [!CODE [VSSDKSignatureHelpTest#5](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#5)]  
  
7.  Добавьте несколько закрытых полей.  
  
     [!CODE [VSSDKSignatureHelpTest#6](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#6)]  
  
8.  Добавьте конструктор, который задает поля и подписывается на <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> события.  
  
     [!CODE [VSSDKSignatureHelpTest#7](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#7)]  
  
9. Объявите `CurrentParameterChanged` события. Это событие возникает, когда пользователь заполняет один из параметров в сигнатуре.  
  
     [!CODE [VSSDKSignatureHelpTest#8](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#8)]  
  
10. Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.CurrentParameter%2A> свойство, так что он вызывает `CurrentParameterChanged` событие при изменении значения свойства.  
  
     [!CODE [VSSDKSignatureHelpTest#9](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#9)]  
  
11. Добавьте метод, который вызывает `CurrentParameterChanged` события.  
  
     [!CODE [VSSDKSignatureHelpTest#10](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#10)]  
  
12. Добавьте метод, который вычисляет параметр текущего числа запятых в <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A> число запятых в сигнатуре.  
  
     [!CODE [VSSDKSignatureHelpTest#11](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#11)]  
  
13. Добавьте обработчик событий для <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> событие, которое вызывает `ComputeCurrentParameter()` метод.  
  
     [!CODE [VSSDKSignatureHelpTest#12](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#12)]  
  
14. Реализуйте свойство <xref:Microsoft.VisualStudio.Language.Intellisense.ISignature.ApplicableToSpan%2A>. Это свойство содержит <xref:Microsoft.VisualStudio.Text.ITrackingSpan> соответствующий диапазон текста в буфере, к которому относится подпись.  
  
     [!CODE [VSSDKSignatureHelpTest#13](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#13)]  
  
15. Реализуйте другие параметры.  
  
     [!CODE [VSSDKSignatureHelpTest#14](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#14)]  
  
## Реализация источника справка сигнатуры  
 Справка по сигнатурам источником является набор сигнатур, для которых задаются сведения.  
  
#### Для реализации источника справка сигнатуры  
  
1.  Добавьте класс с именем `TestSignatureHelpSource` реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource>.  
  
     [!CODE [VSSDKSignatureHelpTest#15](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#15)]  
  
2.  Добавьте ссылку в текстовом буфере.  
  
     [!CODE [VSSDKSignatureHelpTest#16](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#16)]  
  
3.  Добавьте конструктор, который задает текстовый буфер и поставщик источника справка сигнатуры.  
  
     [!CODE [VSSDKSignatureHelpTest#17](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#17)]  
  
4.  Выполните метод <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.AugmentSignatureHelpSession%2A>. В этом примере подписи жестко запрограммированы, но в полной реализации бы получить эту информацию из документации по языку.  
  
     [!CODE [VSSDKSignatureHelpTest#18](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#18)]  
  
5.  Вспомогательный метод `CreateSignature()` предоставляется только для иллюстрации.  
  
     [!CODE [VSSDKSignatureHelpTest#19](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#19)]  
  
6.  Выполните метод <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSource.GetBestMatch%2A>. В этом примере существует всего две подписи, каждый из которых имеет два параметра. Таким образом этот метод не требуется. В более полной реализации, в которой доступно более одного источника справка сигнатуры, этот метод используется, следует ли источника справка сигнатуры наивысший приоритет можно указать совпадающей сигнатурой. В противном случае метод возвращает значение null, и далее наивысшим приоритетом источника должна предоставить совпадение.  
  
     [!CODE [VSSDKSignatureHelpTest#20](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#20)]  
  
7.  Реализуйте метод Dispose\(\):  
  
     [!CODE [VSSDKSignatureHelpTest#21](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#21)]  
  
## Реализация поставщика источника справка сигнатуры  
 Поставщик источника справка сигнатуры отвечает экспорта компонента Managed Extensibility Framework \(MEF\), а также для создания источника справка сигнатуры.  
  
#### Реализация поставщика источника справка сигнатуры  
  
1.  Добавьте класс с именем `TestSignatureHelpSourceProvider` реализующий <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider>, и экспортировать его с <xref:Microsoft.VisualStudio.Utilities.NameAttribute>,  <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> «текст» и <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> из ранее \= «по умолчанию».  
  
     [!CODE [VSSDKSignatureHelpTest#22](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#22)]  
  
2.  Реализуйте <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpSourceProvider.TryCreateSignatureHelpSource%2A> путем создания экземпляра `TestSignatureHelpSource`.  
  
     [!CODE [VSSDKSignatureHelpTest#23](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#23)]  
  
## Реализация обработчика команды  
 Справка сигнатуры обычно инициируется \(символьных и отключенные по\) символов. Можно обработать эти нажатия клавиш, реализовав <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> таким образом, чтобы он инициирует сеанс справки сигнатуры, при получении \(символ предшествует имя известного метода и закрывает сеанс, когда он получает\) символов.  
  
#### Для реализации обработчика команды  
  
1.  Добавьте класс с именем `TestSignatureHelpCommand` реализующий <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!CODE [VSSDKSignatureHelpTest#24](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#24)]  
  
2.  Добавьте закрытые поля для <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> адаптера \(который позволяет добавлять обработчик команды в цепочке управления обработчики\), текстовое представление, справка сигнатуры посредника и сеансов, <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigator>, и следующим <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.  
  
     [!CODE [VSSDKSignatureHelpTest#25](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#25)]  
  
3.  Добавьте конструктор для инициализации эти поля и добавить фильтр команды в цепочке управления фильтры.  
  
     [!CODE [VSSDKSignatureHelpTest#26](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#26)]  
  
4.  Реализуйте <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> метод для запуска сеанса справки сигнатуры, при получении команды фильтр \(символ после имен известных методов, а также для закрытия сеанса, при получении\) символов, пока сеанс еще активен. В каждом случае перенаправляется команда.  
  
     [!CODE [VSSDKSignatureHelpTest#27](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#27)]  
  
5.  Реализация <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> метода, так что он всегда отправляет команду.  
  
     [!CODE [VSSDKSignatureHelpTest#28](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#28)]  
  
## Реализация поставщика команду Help подписи  
 Можно предоставить команде Help подпись путем реализации <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> для создания экземпляра обработчика команды при создании представления текста.  
  
#### Реализация поставщика команду Справка сигнатуры  
  
1.  Добавьте класс с именем `TestSignatureHelpController` реализующий <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> и экспортировать его с <xref:Microsoft.VisualStudio.Utilities.NameAttribute>, <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>, и <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>.  
  
     [!CODE [VSSDKSignatureHelpTest#29](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#29)]  
  
2.  Импорт <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> \(используется для получения <xref:Microsoft.VisualStudio.Text.Editor.ITextView>, присвоенный <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> объекта\), <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> \(используется для поиска текущего слова\) и <xref:Microsoft.VisualStudio.Language.Intellisense.ISignatureHelpBroker> \(для запуска сеанса справки сигнатуры\).  
  
     [!CODE [VSSDKSignatureHelpTest#30](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#30)]  
  
3.  Реализация <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener.VsTextViewCreated%2A> метода путем создания экземпляра `TestSignatureCommandHandler`.  
  
     [!CODE [VSSDKSignatureHelpTest#31](../CodeSnippet/VS_Snippets_VSSDK/vssdksignaturehelptest#31)]  
  
## Сборка и тестирование кода  
 Чтобы проверить код, создания SignatureHelpTest решения и запустите его в экспериментальном экземпляре.  
  
#### Для построения и тестирования решений SignatureHelpTest  
  
1.  Постройте решение.  
  
2.  При запуске этого проекта в отладчике создается второй экземпляр Visual Studio.  
  
3.  Создайте текстовый файл и введите текст, который включает слово «добавить», а также открывающую скобку.  
  
4.  После ввода открывающей скобки, вы увидите подсказку, которая отображает список две подписи `add()` метод.  
  
## См. также  
 [Пошаговое руководство: Связывание типа контента с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
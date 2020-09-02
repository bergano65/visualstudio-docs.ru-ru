---
title: Пошаговое руководство. Отображение парных скобок | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: caaafd0143d3b09a51518ee5f54a02b06dbf10aa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68165779"
---
# <a name="walkthrough-displaying-matching-braces"></a>Пошаговое руководство. Отображение парных фигурных скобок
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно реализовать языковые функции, такие как Парные фигурные скобки, определив фигурные скобки, которые нужно сопоставить, а затем добавив тег текстового маркера к парным фигурным скобкам, если курсор находится на одной из фигурных скобок. Можно определить фигурные скобки в контексте языка или определить собственное расширение имени файла и тип содержимого, а также применить теги только к этому типу или применить теги к существующему типу содержимого (например, "Text"). В следующем пошаговом руководстве показано, как применить теги сопоставления фигурных скобок к типу содержимого text.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Кроме того, пакет SDK для VS можно установить позже. Дополнительные сведения см. [в разделе Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Создание проекта Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Создание проекта MEF  
  
1. Создайте проект классификатора редактора. Назовите решение `BraceMatchingTest`.  
  
2. Добавьте шаблон элемента классификатора редактора в проект. Дополнительные сведения см. в разделе [Создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Удалите файлы существующих классов.  
  
## <a name="implementing-a-brace-matching-tagger"></a>Реализация тегов для сопоставления фигурных скобок  
 Чтобы получить маркер выделения фигурных скобок, похожий на тот, который используется в Visual Studio, можно реализовать средство создания тегов типа <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> . В следующем коде показано, как определить средство создания тегов для пар скобок на любом уровне вложенности. В этом примере пары фигурных скобок []. [] и {} определены в конструкторе тегов, но в полной реализации языка соответствующие пары фигурных скобок будут определены в спецификации языка.  
  
#### <a name="to-implement-a-brace-matching-tagger"></a>Реализация тегов для сопоставления фигурных скобок  
  
1. Добавьте файл класса и назовите его цветность.  
  
2. Импортируйте следующие пространства имен.  
  
     [!code-csharp[VSSDKBraceMatchingTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#1)]
     [!code-vb[VSSDKBraceMatchingTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#1)]  
  
3. Определите класс `BraceMatchingTagger` , наследующий от <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> типа <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .  
  
     [!code-csharp[VSSDKBraceMatchingTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#2)]
     [!code-vb[VSSDKBraceMatchingTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#2)]  
  
4. Добавьте свойства для текстового представления, исходного буфера и текущей точки моментального снимка, а также набор пар фигурных скобок.  
  
     [!code-csharp[VSSDKBraceMatchingTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#3)]
     [!code-vb[VSSDKBraceMatchingTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#3)]  
  
5. В конструкторе тегов укажите свойства и подпишитесь на события изменения представления <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> и <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> . В этом примере для демонстрационных целей в конструкторе также определяются совпадающие пары.  
  
     [!code-csharp[VSSDKBraceMatchingTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#4)]
     [!code-vb[VSSDKBraceMatchingTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#4)]  
  
6. В рамках <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> реализации объявите событие тагсчанжед.  
  
     [!code-csharp[VSSDKBraceMatchingTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#5)]
     [!code-vb[VSSDKBraceMatchingTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#5)]  
  
7. Обработчики событий обновляют текущую позиции курсора `CurrentChar` Свойства и вызывают событие тагсчанжед.  
  
     [!code-csharp[VSSDKBraceMatchingTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#6)]
     [!code-vb[VSSDKBraceMatchingTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#6)]  
  
8. Реализуйте <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> метод для сопоставления фигурных скобок, если текущий символ является открывающей фигурной скобкой или если предыдущий символ является закрывающей фигурной скобкой, как в Visual Studio. При обнаружении совпадения этот метод создает два тега: один для открывающей фигурной скобки, а другой — для закрывающей.  
  
     [!code-csharp[VSSDKBraceMatchingTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#7)]
     [!code-vb[VSSDKBraceMatchingTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#7)]  
  
9. Следующие закрытые методы находят парную фигурную скобку на любом уровне вложенности. Первый метод находит символ закрытия, соответствующий открывающему символу:  
  
     [!code-csharp[VSSDKBraceMatchingTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#8)]
     [!code-vb[VSSDKBraceMatchingTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#8)]  
  
10. Следующий вспомогательный метод находит открытый символ, соответствующий закрывающему символу:  
  
     [!code-csharp[VSSDKBraceMatchingTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#9)]
     [!code-vb[VSSDKBraceMatchingTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#9)]  
  
## <a name="implementing-a-brace-matching-tagger-provider"></a>Реализация поставщика тегов для сопоставления фигурных скобок  
 Помимо реализации средства создания тегов, необходимо также реализовать и экспортировать поставщик тегов. В этом случае тип содержимого поставщика — Text. Это означает, что Парные фигурные скобки будут отображаться во всех типах текстовых файлов, но более полное применение будет применять сопоставление фигурных скобок только с конкретным типом содержимого.  
  
#### <a name="to-implement-a-brace-matching-tagger-provider"></a>Реализация поставщика тегов для сопоставления фигурных скобок  
  
1. Объявите поставщик тегов, наследующий от <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider> , назовите его брацематчингтагжерпровидер и экспортируйте его с помощью <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Text" и объекта <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> .  
  
     [!code-csharp[VSSDKBraceMatchingTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#10)]
     [!code-vb[VSSDKBraceMatchingTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#10)]  
  
2. Реализуйте <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> метод для создания экземпляра брацематчингтагжер.  
  
     [!code-csharp[VSSDKBraceMatchingTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#11)]
     [!code-vb[VSSDKBraceMatchingTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#11)]  
  
## <a name="building-and-testing-the-code"></a>Сборка и тестирование кода  
 Чтобы протестировать этот код, создайте решение Брацематчингтест и запустите его в экспериментальном экземпляре.  
  
#### <a name="to-build-and-test-bracematchingtest-solution"></a>Создание и тестирование решения Брацематчингтест  
  
1. Создайте решение.  
  
2. При запуске этого проекта в отладчике создается второй экземпляр Visual Studio.  
  
3. Создайте текстовый файл и введите текст, содержащий Парные фигурные скобки.  
  
    ```  
    hello {  
    goodbye}  
  
    {}  
  
    {hello}  
    ```  
  
4. При размещении курсора перед открывающей фигурной скобкой следует выделить обе фигурные скобки и соответствующую закрывающую фигурную скобку. При размещении курсора сразу после закрывающей скобки должны быть выделены как фигурные скобки, так и парные открывающие скобки.  
  
## <a name="see-also"></a>См. также:  
 [Пошаговое руководство. Связывание типа контента с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)

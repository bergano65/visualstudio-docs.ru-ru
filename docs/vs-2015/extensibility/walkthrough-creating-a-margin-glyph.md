---
title: 'Пошаговое руководство: Создание глифа поля | Документация Майкрософт'
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
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
caps.latest.revision: 30
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 83b721c7b0ac33d9a37d9705cd780edcd591d9aa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47562879"
---
# <a name="walkthrough-creating-a-margin-glyph"></a>Пошаговое руководство. Создание глифа поля
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Пошаговое руководство: создание глифа поля](https://docs.microsoft.com/visualstudio/extensibility/walkthrough-creating-a-margin-glyph).  
  
Можно настроить внешний вид поля редактора с помощью расширения пользовательского редактора. В этом пошаговом руководстве помещает пользовательского глифа в поле индикаторов, каждый раз, когда отображается слово «todo» в комментарии к коду.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не следует устанавливать пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Создание проекта MEF  
  
1.  Создайте проект VSIX C#. (В **новый проект** диалоговом окне выберите **Visual C# / Extensibility**, затем **проект VSIX**.) Назовите решение `TodoGlyphTest`.  
  
2.  Добавьте элемент проект классификатора редактора. Дополнительные сведения см. в разделе [создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Удалите файлы существующих классов.  
  
## <a name="defining-the-glyph"></a>Определение глифа  
 Определите глиф, реализовав <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> интерфейс.  
  
#### <a name="to-define-the-glyph"></a>Для определения глифа  
  
1.  Добавьте файл класса и назовите его `TodoGlyphFactory`.  
  
2.  Добавьте следующий код с помощью объявлений.  
  
     [!code-csharp[VSSDKTodoGlyphTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#1)]
     [!code-vb[VSSDKTodoGlyphTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#1)]  
  
3.  Добавьте класс с именем `TodoGlyphFactory` , реализующий <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>.  
  
     [!code-csharp[VSSDKTodoGlyphTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#2)]
     [!code-vb[VSSDKTodoGlyphTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#2)]  
  
4.  Добавьте закрытое поле, которое определяет размеры глифа.  
  
     [!code-csharp[VSSDKTodoGlyphTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#3)]
     [!code-vb[VSSDKTodoGlyphTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#3)]  
  
5.  Реализуйте `GenerateGlyph` , определяя элемент пользовательского интерфейса (UI) глифа. `TodoTag` будет рассматриваться далее в этом пошаговом руководстве.  
  
     [!code-csharp[VSSDKTodoGlyphTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#4)]
     [!code-vb[VSSDKTodoGlyphTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#4)]  
  
6.  Добавьте класс с именем `TodoGlyphFactoryProvider` , реализующий <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>. Экспорт этого класса с <xref:Microsoft.VisualStudio.Utilities.NameAttribute> из «TodoGlyph», <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> из после VsTextMarker <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> «код» и <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> из TodoTag.  
  
     [!code-csharp[VSSDKTodoGlyphTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#5)]
     [!code-vb[VSSDKTodoGlyphTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#5)]  
  
7.  Реализуйте <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> метод путем создания экземпляра `TodoGlyphFactory`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#6)]
     [!code-vb[VSSDKTodoGlyphTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#6)]  
  
## <a name="defining-a-todo-tag-and-tagger"></a>Определение тега Todo и средство создания тегов  
 Определите связь между элементом пользовательского интерфейса, определенные на предыдущих шагах и поле индикаторов, создать тип тега и средство создания тегов или экспортировать его с помощью поставщика разметчика.  
  
#### <a name="to-define-a-todo-tag-and-tagger"></a>Для определения тега todo и средство создания тегов  
  
1.  Добавьте новый файл класса в проект и назовите его `TodoTagger`.  
  
2.  Добавьте следующие импорты.  
  
     [!code-csharp[VSSDKTodoGlyphTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#7)]
     [!code-vb[VSSDKTodoGlyphTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#7)]  
  
3.  Добавьте класс с именем `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#8)]
     [!code-vb[VSSDKTodoGlyphTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#8)]  
  
4.  Измените класс с именем `TodoTagger` , реализующий <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> типа `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#9)]
     [!code-vb[VSSDKTodoGlyphTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#9)]  
  
5.  Для `TodoTagger` класса, добавьте закрытые поля для <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> и текст для поиска в данной классификации диапазонами.  
  
     [!code-csharp[VSSDKTodoGlyphTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#10)]
     [!code-vb[VSSDKTodoGlyphTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#10)]  
  
6.  Добавьте конструктор, который задает классификатора.  
  
     [!code-csharp[VSSDKTodoGlyphTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#11)]
     [!code-vb[VSSDKTodoGlyphTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#11)]  
  
7.  Реализуйте <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> метод путем нахождения всех классификации охватывает, имена которых содержат слово «comment» и текст которого включает в себя текст для поиска. Каждый раз, когда найден искомый текст обратно yield новый <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> типа `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#12)]
     [!code-vb[VSSDKTodoGlyphTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#12)]  
  
8.  Объявите `TagsChanged` событий.  
  
     [!code-csharp[VSSDKTodoGlyphTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#13)]
     [!code-vb[VSSDKTodoGlyphTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#13)]  
  
9. Добавьте класс с именем `TodoTaggerProvider` , реализующий <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>и экспортировать его с <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> из «код» и <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> из TodoTag.  
  
     [!code-csharp[VSSDKTodoGlyphTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#14)]
     [!code-vb[VSSDKTodoGlyphTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#14)]  
  
10. Импорт <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>.  
  
     [!code-csharp[VSSDKTodoGlyphTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#15)]
     [!code-vb[VSSDKTodoGlyphTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#15)]  
  
11. Реализуйте <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> метод путем создания экземпляра `TodoTagger`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#16)]
     [!code-vb[VSSDKTodoGlyphTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#16)]  
  
## <a name="building-and-testing-the-code"></a>Сборка и тестирование кода  
 Чтобы протестировать этот код, выполните сборку решения TodoGlyphTest и запустите его в экспериментальном экземпляре.  
  
#### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Построение и тестирование решения TodoGlyphTest  
  
1.  Постройте решение.  
  
2.  Запустите проект, нажав клавишу F5. Создается второй экземпляр Visual Studio.  
  
3.  Убедитесь, что отображается поле индикаторов. (На **средства** меню, щелкните **параметры**. На **текстовый редактор** странице, убедитесь, что **индикаторов** выбран.)  
  
4.  Откройте файл кода, который содержит комментариев. Добавление слова «todo» в разделах комментарий.  
  
5.  В поле индикаторов слева от окна кода появится светлой голубой круг, который имеет Темно-синий контур.


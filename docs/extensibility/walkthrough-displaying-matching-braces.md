---
title: 'Пошаговое руководство: Отображение парных скобок | Документация Майкрософт'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1f29596c95646db78145725f1f0cead424e1de5e
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500440"
---
# <a name="walkthrough-display-matching-braces"></a>Пошаговое руководство: Отображение парных фигурных скобок
Внедрение возможностей языка, например парные фигурные скобки, определение фигурные скобки, которые вы хотите обеспечить поиск и добавив тег текстовой метки парные фигурные скобки, когда курсор находится на одном фигурных скобок. Можно определить фигурные скобки в контексте языка, определите расширение имени файла и тип содержимого и применить теги к только что, введите или применить теги к существующему типу содержимого (например, «text»). Следующие пошаговом руководстве показано, как применить парные фигурные скобки теги к типу содержимого «text».  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не устанавливайте Visual Studio SDK в центре загрузки. Этот пакет включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установить пакет SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="create-a-managed-extensibility-framework-mef-project"></a>Создание проекта Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Создание проекта MEF  
  
1.  Создайте проект классификатора редактора. Назовите решение `BraceMatchingTest`.  
  
2.  Добавьте в проект шаблон элемента классификатора редактора. Дополнительные сведения см. в разделе [создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Удалите файлы существующих классов.  
  
## <a name="implement-a-brace-matching-tagger"></a>Реализовать парные средство создания тегов  
 Чтобы получить Выделение скобок подсветкой эффект, похожий на тот, который используется в Visual Studio, можно реализовать средство создания тегов типа <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>. Ниже показано, как определить средство создания тегов для наглядной на любом уровне вложенности. В этом примере пары скобок [] и {} определяются в конструкторе средство создания тегов, а также в полной реализацией языка, соответствующего фигурную скобку, пары "должны быть определены в спецификации языка.  
  
### <a name="to-implement-a-brace-matching-tagger"></a>Для реализации парные средство создания тегов  
  
1.  Добавьте файл класса и назовите его цветность, соответствие скобок.  
  
2.  Импортируйте следующие пространства имен.  
  
     [!code-csharp[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]  
  
3.  Определите класс `BraceMatchingTagger` , наследуемый от <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> типа <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-csharp[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]  
  
4.  Добавьте свойства для представления текста, исходного буфера, текущей точки моментальных снимков, а также набор пар скобок.  
  
     [!code-csharp[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]  
  
5.  В конструкторе средство создания тегов, задайте свойства и подписываться на события изменения представления <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> и <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>. В этом примере для иллюстрации, совпадающие пары также определены в конструкторе.  
  
     [!code-csharp[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]  
  
6.  Как часть <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> реализации, объявить событие TagsChanged.  
  
     [!code-csharp[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]  
  
7.  Обработчики событий обновить текущую позицию курсора `CurrentChar` свойство и порождения событий TagsChanged.  
  
     [!code-csharp[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]  
  
8.  Реализуйте <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> метода в соответствии фигурные скобки, либо когда текущий символ является открывающую фигурную скобку, или когда предыдущий символ — это закрывающей фигурной скобки, как в Visual Studio. Если совпадение найдено, этот метод создает два тега, один для открывающую фигурную скобку, а другой для закрывающей фигурной скобки.  
  
     [!code-csharp[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]  
  
9. Следующие закрытые методы Поиск парной скобке на любом уровне вложенности. Первый метод находит закрыть символ, который соответствует символу открыть:  
  
     [!code-csharp[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]  
  
10. Следующий вспомогательный метод находит откройте символ, который соответствует символу закрыть:  
  
     [!code-csharp[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]  
  
## <a name="implement-a-brace-matching-tagger-provider"></a>Реализация поставщика сопоставления средство создания тегов фигурная скобка  
 Помимо реализации средство создания тегов, необходимо также реализовать и экспортировать поставщика разметчика. В этом случае тип содержимого поставщика — «text». Таким образом парные фигурные скобки будут отображаться во всех типах текстовых файлов, но более полной реализации применяется парные фигурные скобки только к определенному типу содержимого.  
  
### <a name="to-implement-a-brace-matching-tagger-provider"></a>Для реализации поставщика сопоставления средство создания тегов фигурная скобка  
  
1.  Объявите поставщика, средство создания тегов, который наследует от <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>, назовите его BraceMatchingTaggerProvider и экспортировать его с <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> «текст» и <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> из <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-csharp[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]  
  
2.  Реализуйте <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> метод для создания экземпляра BraceMatchingTagger.  
  
     [!code-csharp[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]  
  
## <a name="build-and-test-the-code"></a>Построение и тестирование кода  
 Чтобы протестировать этот код, выполните сборку решения BraceMatchingTest и запустите его в экспериментальном экземпляре.  
  
#### <a name="to-build-and-test-bracematchingtest-solution"></a>Построение и тестирование решения BraceMatchingTest  
  
1.  Постройте решение.  
  
2.  При запуске этого проекта в отладчике, запускается второй экземпляр Visual Studio.  
  
3.  Создайте текстовый файл и введите текст, который включает в себя парные фигурные скобки.  
  
    ```  
    hello {  
    goodbye}  
  
    {}  
  
    {hello}  
    ```  
  
4.  Если поместить курсор перед открывающую фигурную скобку, должны быть выделены, фигурную скобку и сопоставления закрывающей фигурной скобки. Если поместить курсор сразу после закрывающей фигурной скобки, должны быть выделены, фигурную скобку и сопоставления открывающую фигурную скобку.  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство: Связывание типа контента с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
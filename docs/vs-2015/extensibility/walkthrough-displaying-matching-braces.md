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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "68165779"
---
# <a name="walkthrough-displaying-matching-braces"></a>Пошаговое руководство. Отображение парных скобок
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Вы можете реализовать на базе языка функции, такие как парные фигурные скобки путем определения фигурные скобки, которые вы хотите обеспечить поиск и затем добавление тег текстовой метки в парные фигурные скобки, когда курсор находится на одном фигурных скобок. Фигурные скобки можно определить в контексте языка, можно определить тип имени собственного файла расширения и содержимого и применить теги к только этого типа или можно применить теги к существующий тип контента (например, «text»). Следующие пошаговом руководстве показано, как применить парные фигурные скобки теги к типу содержимого «text».  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не следует устанавливать пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Создание проекта Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Создание проекта MEF  
  
1. Создайте проект классификатора редактора. Назовите решение `BraceMatchingTest`.  
  
2. Добавьте в проект шаблон элемента классификатора редактора. Дополнительные сведения см. в разделе [создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Удалите файлы существующих классов.  
  
## <a name="implementing-a-brace-matching-tagger"></a>Реализация парные средство создания тегов  
 Чтобы получить Выделение скобок подсветкой эффект, похожий на тот, который используется в Visual Studio, можно реализовать средство создания тегов типа <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>. Ниже показано, как определить средство создания тегов для наглядной на любом уровне вложенности. В этом примере саму фигурную скобку в виде пары []. [], и {} определяются в конструкторе средство создания тегов, а также в полной реализацией языка соответствующие наглядной должны быть определены в спецификации языка.  
  
#### <a name="to-implement-a-brace-matching-tagger"></a>Для реализации парные средство создания тегов  
  
1. Добавьте файл класса и назовите его цветность, соответствие скобок.  
  
2. Импортируйте следующие пространства имен.  
  
     [!code-csharp[VSSDKBraceMatchingTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#1)]
     [!code-vb[VSSDKBraceMatchingTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#1)]  
  
3. Определите класс `BraceMatchingTagger` , наследуемый от <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> типа <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-csharp[VSSDKBraceMatchingTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#2)]
     [!code-vb[VSSDKBraceMatchingTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#2)]  
  
4. Добавьте свойства для представления текста, исходного буфера и текущую точку моментального снимка, а также набор пар скобок.  
  
     [!code-csharp[VSSDKBraceMatchingTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#3)]
     [!code-vb[VSSDKBraceMatchingTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#3)]  
  
5. В конструкторе средство создания тегов, задайте свойства и подписываться на события изменения представления <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> и <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>. В этом примере для иллюстрации, совпадающие пары также определены в конструкторе.  
  
     [!code-csharp[VSSDKBraceMatchingTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#4)]
     [!code-vb[VSSDKBraceMatchingTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#4)]  
  
6. Как часть <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> реализации, объявить событие TagsChanged.  
  
     [!code-csharp[VSSDKBraceMatchingTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#5)]
     [!code-vb[VSSDKBraceMatchingTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#5)]  
  
7. Обработчики событий обновить текущую позицию курсора `CurrentChar` свойство и порождения событий TagsChanged.  
  
     [!code-csharp[VSSDKBraceMatchingTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#6)]
     [!code-vb[VSSDKBraceMatchingTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#6)]  
  
8. Реализуйте <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> метода в соответствии фигурные скобки, либо когда текущий символ является открывающую фигурную скобку, или когда предыдущий символ — это закрывающей фигурной скобки, как в Visual Studio. Если совпадение найдено, этот метод создает два тега, один для открывающую фигурную скобку, а другой для закрывающей фигурной скобки.  
  
     [!code-csharp[VSSDKBraceMatchingTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#7)]
     [!code-vb[VSSDKBraceMatchingTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#7)]  
  
9. Следующие закрытые методы Поиск парной скобке на любом уровне вложенности. Первый метод находит закрыть символ, который соответствует символу открыть:  
  
     [!code-csharp[VSSDKBraceMatchingTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#8)]
     [!code-vb[VSSDKBraceMatchingTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#8)]  
  
10. Следующий вспомогательный метод находит откройте символ, который соответствует символу закрыть:  
  
     [!code-csharp[VSSDKBraceMatchingTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#9)]
     [!code-vb[VSSDKBraceMatchingTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#9)]  
  
## <a name="implementing-a-brace-matching-tagger-provider"></a>Реализация поставщика разметчика парные  
 Помимо реализации средство создания тегов, необходимо также реализовать и экспортировать поставщика разметчика. В этом случае тип содержимого поставщика — «text». Это означает, что парные будет отображаться во всех типах текстовых файлов, но более полной реализации будет применяться парные фигурные скобки только к определенному типу содержимого.  
  
#### <a name="to-implement-a-brace-matching-tagger-provider"></a>Для реализации поставщика сопоставления средство создания тегов фигурная скобка  
  
1. Объявите поставщика, средство создания тегов, который наследует от <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>, назовите его BraceMatchingTaggerProvider и экспортировать его с <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> «текст» и <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> из <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-csharp[VSSDKBraceMatchingTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#10)]
     [!code-vb[VSSDKBraceMatchingTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#10)]  
  
2. Реализуйте <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> метод для создания экземпляра BraceMatchingTagger.  
  
     [!code-csharp[VSSDKBraceMatchingTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdkbracematchingtest/cs/bracematching.cs#11)]
     [!code-vb[VSSDKBraceMatchingTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkbracematchingtest/vb/bracematching.vb#11)]  
  
## <a name="building-and-testing-the-code"></a>Сборка и тестирование кода  
 Чтобы протестировать этот код, выполните сборку решения BraceMatchingTest и запустите его в экспериментальном экземпляре.  
  
#### <a name="to-build-and-test-bracematchingtest-solution"></a>Построение и тестирование решения BraceMatchingTest  
  
1. Постройте решение.  
  
2. При запуске этого проекта в отладчике создается второй экземпляр Visual Studio.  
  
3. Создайте текстовый файл и введите текст, который включает в себя парные фигурные скобки.  
  
    ```  
    hello {  
    goodbye}  
  
    {}  
  
    {hello}  
    ```  
  
4. Если поместить курсор перед открывающую фигурную скобку, должны быть выделены, фигурную скобку и сопоставления закрывающей фигурной скобки. Если поместить курсор сразу после закрывающей фигурной скобки, должны быть выделены, фигурную скобку и сопоставления открывающую фигурную скобку.  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство: связывание типа контента с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)

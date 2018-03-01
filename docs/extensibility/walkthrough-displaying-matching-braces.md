---
title: "Пошаговое руководство: Отображение парные фигурные скобки | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - brace matching
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
caps.latest.revision: 
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: c3dde61c10d0a8c9fc5578b02cc713f648409cbf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-displaying-matching-braces"></a>Пошаговое руководство: Отображение парные фигурные скобки
Можно реализовать функции, основанный на языке, например парные фигурные скобки, определив фигурные скобки, который должен соответствовать и добавив парные фигурные скобки тег текстовой метки, когда курсор находится на одном из фигурные скобки. Фигурные скобки можно определить в контексте языка, можно определить тип имени собственного файла расширения и содержимое и применяются только к этому типу теги или теги можно применить к существующему типу содержимого (например, «текст»). Следующего пошагового руководства демонстрируется применение парные фигурные скобки теги с типом содержимого «text».  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки Майкрософт. Он включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Создание проекта Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Создание проекта MEF  
  
1.  Создайте проект классификатора редактора. Присвойте решению имя `BraceMatchingTest`.  
  
2.  Добавьте в проект шаблон элемента классификатора редактора. Дополнительные сведения см. в разделе [создания расширения с помощью шаблона элемента редактор](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Удалите файлы существующих классов.  
  
## <a name="implementing-a-brace-matching-tagger"></a>Реализация парные фигурные скобки создания тегов  
 Чтобы получить фигурную скобку выделение эффект, похожий того, который используется в Visual Studio, можно реализовать разметчика типа <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>. Ниже показан способ определения разметчика для пар фигурную скобку на любом уровне вложенности. В этом примере [] пары фигурную скобку. [] {} определяются в конструкторе создания тегов, а в реализации полный языковой пары соответствующих фигурная скобка должны быть определены в спецификации языка.  
  
#### <a name="to-implement-a-brace-matching-tagger"></a>Для реализации парные фигурные скобки создания тегов  
  
1.  Добавьте файл класса и назовите его цветность, соответствие скобок.  
  
2.  Импортируйте следующие пространства имен.  
  
     [!code-csharp[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]  
  
3.  Определите класс `BraceMatchingTagger` , наследуемый от <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> типа <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-csharp[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]  
  
4.  Добавьте свойства для представления текста, исходный буфер и текущей точки моментальных снимков, а также набор пар фигурную скобку.  
  
     [!code-csharp[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]  
  
5.  В конструкторе разметчика задайте свойства и подписаться на события изменения представления <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> и <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>. В этом примере для демонстрации, совпадающие пары также определены в конструкторе.  
  
     [!code-csharp[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]  
  
6.  В рамках <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> реализации объявить событие TagsChanged.  
  
     [!code-csharp[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]  
  
7.  Обработчики событий обновления в текущей позиции курсора `CurrentChar` свойства и вызвать событие TagsChanged.  
  
     [!code-csharp[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]  
  
8.  Реализация <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> метода в соответствии фигурные скобки, либо когда текущий символ является открывающую фигурную скобку или в случае предыдущий знак закрывающей фигурной скобки, как в Visual Studio. Если соответствие найдено, этот метод создает два тега, один для открывающую фигурную скобку, а другой для закрывающей фигурной скобки.  
  
     [!code-csharp[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]  
  
9. Следующие методы закрытый Найти парную скобку на любом уровне вложенности. Первый метод находит закрыть символ, который соответствует символу открыть:  
  
     [!code-csharp[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]  
  
10. Следующий вспомогательный метод находит откройте символ, который соответствует символу закрыть:  
  
     [!code-csharp[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]  
  
## <a name="implementing-a-brace-matching-tagger-provider"></a>Реализация парные фигурные скобки поставщика разметчика  
 Помимо реализации разметчика, необходимо также реализовать и экспортировать поставщика разметчика. В этом случае тип содержимого поставщика — «text». Это означает, что парные будет отображаться во всех типах текстовые файлы, но полное реализации они парные фигурные скобки только для определенных типов содержимого.  
  
#### <a name="to-implement-a-brace-matching-tagger-provider"></a>Для реализации поставщика разметчика сопоставления фигурная скобка  
  
1.  Объявите поставщика разметчика, который наследует от <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>, назовите его BraceMatchingTaggerProvider и экспортируйте его с <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> «текст» и <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> из <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-csharp[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]  
  
2.  Реализуйте <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> метод для создания BraceMatchingTagger.  
  
     [!code-csharp[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]  
  
## <a name="building-and-testing-the-code"></a>Сборка и тестирование кода  
 Чтобы проверить код, выполните сборку решения BraceMatchingTest и запустите его в экспериментальном экземпляре.  
  
#### <a name="to-build-and-test-bracematchingtest-solution"></a>Для построения и тестирования решения BraceMatchingTest  
  
1.  Постройте решение.  
  
2.  При запуске этого проекта в отладчике создается второй экземпляр Visual Studio.  
  
3.  Создайте текстовый файл и введите текст, который включает в себя парные фигурные скобки.  
  
    ```  
    hello {  
    goodbye}  
  
    {}  
  
    {hello}  
    ```  
  
4.  Если навести курсор перед открывающую фигурную скобку, должны быть выделены, скобки и сопоставления закрывающей фигурной скобки. Если курсор находится сразу после закрывающей фигурной скобки, будет выделена, скобки и сопоставления открывающую фигурную скобку.  
  
## <a name="see-also"></a>См. также  
 [Пошаговое руководство. Связывание типа контента с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
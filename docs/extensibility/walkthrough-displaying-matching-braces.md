---
title: "Пошаговое руководство: Отображение парные фигурные скобки | Microsoft Docs"
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
  - "редакторы [Visual Studio SDK] новый - парные фигурные скобки"
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
caps.latest.revision: 27
caps.handback.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
---
# Пошаговое руководство: Отображение парные фигурные скобки
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Можно реализовать язык на основе функции, такие как проверка парности фигурных скобок, определив фигурные скобки, необходимо найти и добавляя тег текстовой метки в парные фигурные скобки, когда курсор находится на одном фигурных скобок. Фигурные скобки можно определить в контексте языка, можно определить собственный файл имя расширения или типу содержимого и применить теги только этот тип или можно применить теги к существующий тип содержимого \(например, «текст»\). Следующий пример демонстрируется применение парные теги в тип содержимого «text».  
  
## Обязательные компоненты  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в установку Visual Studio. VS SDK также можно установить позже. Для получения дополнительной информации см. [Установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Создание проекта Managed Extensibility Framework \(MEF\)  
  
#### Создание проекта MEF  
  
1.  Создайте проект классификатора редактора. Присвойте решению имя `BraceMatchingTest`.  
  
2.  Добавьте в проект шаблон элемента редактор классификатора. Дополнительные сведения см. в разделе [Создание расширения с помощью редактора шаблона элемента](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Удалите файлы существующих классов.  
  
## Реализация парные создания тегов  
 Чтобы получить Выделение скобок подсветкой эффект, похожий того, который используется в Visual Studio, можно реализовать средство создания тегов типа <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>. Ниже показано определение создания тегов для пар скобок на любом уровне вложенности. В этом примере \[\] пары скобок. \[\] {} определяются в конструкторе создания тегов, но полной реализацией языка пары соответствующих скобок быть определены в спецификации языка.  
  
#### Для реализации парные создания тегов  
  
1.  Добавьте файл класса и назовите его соответствие скобок.  
  
2.  Импортируйте следующие пространства имен.  
  
     [!code-cs[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]  
  
3.  Определите класс `BraceMatchingTagger` наследуемый от <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> типа <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-cs[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]  
  
4.  Добавьте свойства для представления текста, исходного буфера и текущей точки моментальных снимков, а также набор пар скобок.  
  
     [!code-cs[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]  
  
5.  В конструкторе создания тегов, задайте свойства и подписаться на события изменения представления <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> и <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>. В этом примере для демонстрации, совпадающие пары также определены в конструкторе.  
  
     [!code-cs[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]  
  
6.  Как часть <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> реализации объявить событие TagsChanged.  
  
     [!code-cs[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]  
  
7.  Обработчики событий обновить текущую позицию курсора `CurrentChar` Свойства и вызвать событие TagsChanged.  
  
     [!code-cs[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]  
  
8.  Реализация <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> метода соответствуют фигурные скобки, либо когда текущий символ является открывающей скобки или если предыдущий символ закрывающей фигурной скобки, как в Visual Studio. Если совпадение найдено, этот метод создает два тега: для открывающую фигурную скобку и для закрывающей фигурной скобки.  
  
     [!code-cs[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]  
  
9. Следующие закрытые методы Найти парную скобку на любом уровне вложенности. Первый метод находит закрыть символ, который соответствует символу, откройте:  
  
     [!code-cs[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]  
  
10. Следующий вспомогательный метод находит откройте символ, который соответствует символу закрыть:  
  
     [!code-cs[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]  
  
## Реализация поставщика для создания тегов парные  
 Помимо реализации средство создания тегов, необходимо реализовать и экспортировать поставщика создания тегов. В этом случае содержимое поставщика имеет тип «text». Это означает, что парные фигурные скобки будут отображаться для всех типов текстовых файлов, но более полной реализации будет применяться проверка парности фигурных скобок только к определенному типу содержимого.  
  
#### Для реализации поставщика сопоставления создания тегов фигурную скобку  
  
1.  Объявите создания тегов для поставщика, который наследует от <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>, назовите его BraceMatchingTaggerProvider и экспортировать его с <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> «текст» и <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> из <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-cs[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]  
  
2.  Реализуйте <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> метод для создания экземпляра BraceMatchingTagger.  
  
     [!code-cs[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]  
  
## Сборка и тестирование кода  
 Чтобы проверить код, создания BraceMatchingTest решения и запустите его в экспериментальном экземпляре.  
  
#### Для построения и тестирования решений BraceMatchingTest  
  
1.  Постройте решение.  
  
2.  При запуске этого проекта в отладчике создается второй экземпляр Visual Studio.  
  
3.  Создайте текстовый файл и введите текст, который содержит парные фигурные скобки.  
  
    ```  
    hello {  
    goodbye}  
  
    {}  
  
    {hello}  
    ```  
  
4.  Если поместить курсор перед открывающей скобки, будет выделена, скобки и соответствующей закрывающей фигурной скобки. Если курсор находится сразу после закрывающей фигурной скобки, будет выделена, скобки и сопоставления открывающую фигурную скобку.  
  
## См. также  
 [Пошаговое руководство: Связывание типа контента с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
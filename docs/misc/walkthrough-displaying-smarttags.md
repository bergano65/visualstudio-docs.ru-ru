---
title: "Пошаговое руководство. Отображение смарт-тегов | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "редакторы [пакет SDK для Visual Studio], новинка — смарт-теги"
ms.assetid: 10bb4f69-b259-41f0-b91a-69b04385d9a5
caps.latest.revision: 31
caps.handback.revision: 31
manager: "douge"
---
# Пошаговое руководство. Отображение смарт-тегов
Смарт\-теги устарели и были заменены меню лампочки. См. раздел [Пошаговое руководство: Отображение лампочки предложения](../Topic/Walkthrough:%20Displaying%20Light%20Bulb%20Suggestions.md).  
  
 Смарт\-теги — это теги в тексте, которые можно развернуть, чтобы отобразить набор действий. Например, при переименовании идентификатора, такого как имя переменной, в проекте Visual Basic или Visual C\# под словом появляется красная линия. Если навести на нее указатель, рядом с ним появляется кнопка. Если нажать кнопку, то появляется предлагаемое действие, например **Переименовать IsRead в IsReady**. Если выбрать действие, все упоминания **IsRead** в проекте будут изменены на **IsReady**.  
  
 Хотя смарт\-теги являются частью реализации IntelliSense в редакторе, их можно реализовать путем создания подкласса <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag> и последующей реализации интерфейсов <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> и <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>.  
  
> [!NOTE]
>  Аналогичным образом можно реализовать другие виды тегов.  
  
 В этом пошаговом руководстве показано, как создать смарт\-тег, который отображается в текущем слове и имеет два предлагаемых действия: **Преобразовать в верхний регистр** и **Преобразовать в нижний регистр**.  
  
## Обязательные компоненты  
 Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Дополнительные сведения см. в разделе [SDK для Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## Создание проекта Managed Extensibility Framework \(MEF\)  
  
#### Создание проекта MEF  
  
1.  Создайте проект классификатора редактора. Назовите решение `SmartTagTest`.  
  
2.  Откройте файл source.extension.vsixmanifest в редакторе манифестов VSIX.  
  
3.  Убедитесь в том, что в разделе **Активы** содержится тип `Microsoft.VisualStudio.MefComponent`, в поле **Источник** задано значение `A project in current solution`, а в поле **Проект** задано значение SmartTagTest.dll.  
  
4.  Сохраните и закройте файл source.extension.vsixmanifest.  
  
5.  Добавьте в проект следующую ссылку и задайте для свойства **CopyLocal** значение `false`:  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
6.  Удалите файлы существующих классов.  
  
## Реализация разметчика для смарт\-тегов  
  
#### Реализация разметчика для смарт\-тегов  
  
1.  Добавьте файл класса с именем `TestSmartTag`.  
  
2.  Добавьте следующие импортируемые пространства имен:  
  
     [!code-cs[VSSDKSmartTagTest#1](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_1.cs)]
     [!code-vb[VSSDKSmartTagTest#1](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_1.vb)]  
  
3.  Добавьте класс с именем `TestSmartTag`, производный от <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag>.  
  
     [!code-cs[VSSDKSmartTagTest#2](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_2.cs)]
     [!code-vb[VSSDKSmartTagTest#2](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_2.vb)]  
  
4.  Добавьте конструктор для этого класса, который вызывает базовый конструктор со значением <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType>, равным <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType>, что вызывает подчеркивание первого символа в слове синей линией. \(Если использовать значение <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType>, последний символ в слове будет подчеркиваться красной линией.\)  
  
     [!code-cs[VSSDKSmartTagTest#3](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_3.cs)]
     [!code-vb[VSSDKSmartTagTest#3](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_3.vb)]  
  
5.  Добавьте класс с именем `TestSmartTagger`, который наследуется от <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> типа `TestSmartTag` и реализует <xref:System.IDisposable>.  
  
     [!code-cs[VSSDKSmartTagTest#4](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_4.cs)]
     [!code-vb[VSSDKSmartTagTest#4](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_4.vb)]  
  
6.  Добавьте в класс разметчика указанные ниже закрытые поля.  
  
     [!code-cs[VSSDKSmartTagTest#5](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_5.cs)]
     [!code-vb[VSSDKSmartTagTest#5](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_5.vb)]  
  
7.  Добавьте конструктор, который задает закрытые поля и подписывается на событие <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>.  
  
     [!code-cs[VSSDKSmartTagTest#6](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_6.cs)]
     [!code-vb[VSSDKSmartTagTest#6](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_6.vb)]  
  
8.  Реализуйте <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> для создания тега для текущего слова. \(Этот метод также вызывает закрытый метод `GetSmartTagActions`, о котором рассказывается ниже.\)  
  
     [!code-cs[VSSDKSmartTagTest#7](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_7.cs)]
     [!code-vb[VSSDKSmartTagTest#7](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_7.vb)]  
  
9. Добавьте метод `GetSmartTagActions` для настройки действий, связанных со смарт\-тегом. Сами действия будут реализованы в последующих шагах.  
  
     [!code-cs[VSSDKSmartTagTest#8](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_8.cs)]
     [!code-vb[VSSDKSmartTagTest#8](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_8.vb)]  
  
10. Объявите событие `SmartTagsChanged`.  
  
     [!code-cs[VSSDKSmartTagTest#9](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_9.cs)]
     [!code-vb[VSSDKSmartTagTest#9](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_9.vb)]  
  
11. Реализуйте обработчик событий `OnLayoutChanged` для вызова события `TagsChanged`, которое приводит к вызову <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>.  
  
     [!code-cs[VSSDKSmartTagTest#10](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_10.cs)]
     [!code-vb[VSSDKSmartTagTest#10](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_10.vb)]  
  
12. Реализуйте метод <xref:System.IDisposable.Dispose%2A> так, чтобы он отменял подписку на событие <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>.  
  
     [!code-cs[VSSDKSmartTagTest#11](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_11.cs)]
     [!code-vb[VSSDKSmartTagTest#11](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_11.vb)]  
  
## Реализация поставщика разметчика смарт\-тегов  
  
#### Реализация поставщика разметчика смарт\-тегов  
  
1.  Добавьте класс с именем `TestSmartTagTaggerProvider`, производный от <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>. Экспортируйте его с атрибутом <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> со значением text, атрибутом <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> со значением Before\="default" и атрибутом <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> со значением <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag>.  
  
     [!code-cs[VSSDKSmartTagTest#12](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_12.cs)]
     [!code-vb[VSSDKSmartTagTest#12](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_12.vb)]  
  
2.  Импортируйте <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> как свойство.  
  
     [!code-cs[VSSDKSmartTagTest#13](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_13.cs)]
     [!code-vb[VSSDKSmartTagTest#13](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_13.vb)]  
  
3.  Выполните метод <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A>.  
  
     [!code-cs[VSSDKSmartTagTest#14](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_14.cs)]
     [!code-vb[VSSDKSmartTagTest#14](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_14.vb)]  
  
## Реализация действий смарт\-тега  
  
#### Реализация действий смарт\-тега  
  
1.  Создайте два класса с именами `UpperCaseSmartTagAction` и `LowerCaseSmartTagAction`. В обоих классах реализован интерфейс <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagAction>.  
  
     [!code-cs[VSSDKSmartTagTest#15](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_15.cs)]
     [!code-vb[VSSDKSmartTagTest#15](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_15.vb)]  
  
     [!code-cs[VSSDKSmartTagTest#16](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_16.cs)]
     [!code-vb[VSSDKSmartTagTest#16](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_16.vb)]  
  
 Эти два класса похожи за тем исключением, что один из них вызывает <xref:System.String.ToUpper%2A>, а другой вызывает <xref:System.String.ToLower%2A>. В дальнейших шагах рассматривается создание класса для действия преобразования в верхний регистр, но вам необходимо реализовать оба класса. Используйте инструкции по реализации действия преобразования в верхний регистр в качестве шаблона для реализации действия преобразования в нижний регистр.  
  
1.  Объявите набор закрытых полей.  
  
     [!code-cs[VSSDKSmartTagTest#17](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_17.cs)]
     [!code-vb[VSSDKSmartTagTest#17](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_17.vb)]  
  
2.  Добавьте конструктор, который задает поля.  
  
     [!code-cs[VSSDKSmartTagTest#18](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_18.cs)]
     [!code-vb[VSSDKSmartTagTest#18](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_18.vb)]  
  
3.  Реализуйте свойства указанным ниже образом.  
  
     [!code-cs[VSSDKSmartTagTest#19](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_19.cs)]
     [!code-vb[VSSDKSmartTagTest#19](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_19.vb)]  
  
4.  Реализуйте метод <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagAction.Invoke%2A>, заменив текст в диапазоне на эквивалентный текст в верхнем регистре.  
  
     [!code-cs[VSSDKSmartTagTest#20](../misc/codesnippet/CSharp/walkthrough-displaying-smarttags_20.cs)]
     [!code-vb[VSSDKSmartTagTest#20](../misc/codesnippet/VisualBasic/walkthrough-displaying-smarttags_20.vb)]  
  
## Сборка и тестирование кода  
 Чтобы проверить код, выполните сборку решения SmartTagTest и запустите его в экспериментальном экземпляре.  
  
#### Сборка и тестирование решения SmartTagTest  
  
1.  Постройте решение.  
  
2.  При запуске этого проекта в отладчике создается второй экземпляр Visual Studio.  
  
3.  Создайте текстовый файл и введите любой текст.  
  
     Первая буква в первом слове текста должна быть подчеркнута синей линией.  
  
4.  Наведите указатель на синюю линию.  
  
     Рядом с указателем должна появиться кнопка.  
  
5.  Если нажать кнопку, должны отобразиться два предлагаемых действия: **Преобразовать в верхний регистр** и **Преобразовать в нижний регистр**. Если выбрать первое действие, все символы текущего слова должны преобразоваться в верхний регистр. Если выбрать второе действие, все символы должны преобразоваться в нижний регистр.  
  
## См. также  
 [Пошаговое руководство: Связывание типа контента с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
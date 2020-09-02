---
title: Пошаговое руководство. Отображение Смарттагс | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - smart tags
ms.assetid: 10bb4f69-b259-41f0-b91a-69b04385d9a5
caps.latest.revision: 31
manager: jillfra
ms.openlocfilehash: 116f76324a2150413c0ae6d08bc99e114efcc50e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "64805582"
---
# <a name="walkthrough-displaying-smarttags"></a>Пошаговое руководство. Отображение смарт-тегов
Смарт-теги устарели и были заменены меню лампочки. См. раздел [Walkthrough: Displaying Light Bulb Suggestions](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).  
  
 Смарт-теги — это теги в тексте, которые можно развернуть, чтобы отобразить набор действий. Например, при переименовании идентификатора, такого как имя переменной, в проекте Visual Basic или Visual C# под словом появляется красная линия. Если навести на нее указатель, рядом с ним появляется кнопка. Если нажать кнопку, то появляется предлагаемое действие, например **Переименовать IsRead в IsReady**. Если выбрать действие, все упоминания **IsRead** в проекте будут изменены на **IsReady**.  
  
 Хотя смарт-теги являются частью реализации IntelliSense в редакторе, их можно реализовать путем создания подкласса <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag> и последующей реализации интерфейсов <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> и <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>.  
  
> [!NOTE]
> Аналогичным образом можно реализовать другие виды тегов.  
  
 В этом пошаговом руководстве показано, как создать смарт-тег, который отображается в текущем слове и имеет два предлагаемых действия: **Преобразовать в верхний регистр** и **Преобразовать в нижний регистр**.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Для выполнения этого пошагового руководства необходимо установить пакет SDK для Visual Studio. Дополнительные сведения см. в разделе [пакет SDK для Visual Studio](../extensibility/visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Создание проекта Managed Extensibility Framework (MEF)  
  
#### <a name="to-create-a-mef-project"></a>Создание проекта MEF  
  
1. Создайте проект классификатора редактора. Назовите решение `SmartTagTest`.  
  
2. Откройте файл source.extension.vsixmanifest в редакторе манифестов VSIX.  
  
3. Убедитесь в том, что в разделе **Активы** содержится тип `Microsoft.VisualStudio.MefComponent` , в поле **Источник** задано значение `A project in current solution`, а в поле **Проект** задано значение SmartTagTest.dll.  
  
4. Сохраните и закройте файл source.extension.vsixmanifest.  
  
5. Добавьте в проект следующую ссылку и задайте для свойства **CopyLocal** значение `false`:  
  
     Microsoft.VisualStudio.Language.Intellisense  
  
6. Удалите файлы существующих классов.  
  
## <a name="implementing-a-tagger-for-smart-tags"></a>Реализация разметчика для смарт-тегов  
  
#### <a name="to-implement-a-tagger-for-smart-tags"></a>Реализация разметчика для смарт-тегов  
  
1. Добавьте файл класса с именем `TestSmartTag`.  
  
2. Добавьте приведенные ниже определения import:  
  
     [!code-csharp[VSSDKSmartTagTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#1)]
     [!code-vb[VSSDKSmartTagTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#1)]  
  
3. Добавьте класс с именем `TestSmartTag`, производный от <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag>.  
  
     [!code-csharp[VSSDKSmartTagTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#2)]
     [!code-vb[VSSDKSmartTagTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#2)]  
  
4. Добавьте конструктор для этого класса, который вызывает базовый конструктор со значением <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType>, равным <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType>, что вызывает подчеркивание первого символа в слове синей линией. (Если использовать значение <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTagType>, последний символ в слове будет подчеркиваться красной линией.)  
  
     [!code-csharp[VSSDKSmartTagTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#3)]
     [!code-vb[VSSDKSmartTagTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#3)]  
  
5. Добавьте класс с именем `TestSmartTagger`, который наследуется от <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> типа `TestSmartTag` и реализует <xref:System.IDisposable>.  
  
     [!code-csharp[VSSDKSmartTagTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#4)]
     [!code-vb[VSSDKSmartTagTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#4)]  
  
6. Добавьте в класс разметчика указанные ниже закрытые поля.  
  
     [!code-csharp[VSSDKSmartTagTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#5)]
     [!code-vb[VSSDKSmartTagTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#5)]  
  
7. Добавьте конструктор, который задает закрытые поля и подписывается на событие <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>.  
  
     [!code-csharp[VSSDKSmartTagTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#6)]
     [!code-vb[VSSDKSmartTagTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#6)]  
  
8. Реализуйте <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> для создания тега для текущего слова. (Этот метод также вызывает закрытый метод `GetSmartTagActions` , о котором рассказывается ниже.)  
  
     [!code-csharp[VSSDKSmartTagTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#7)]
     [!code-vb[VSSDKSmartTagTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#7)]  
  
9. Добавьте метод `GetSmartTagActions` для настройки действий, связанных со смарт-тегом. Сами действия будут реализованы в последующих шагах.  
  
     [!code-csharp[VSSDKSmartTagTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#8)]
     [!code-vb[VSSDKSmartTagTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#8)]  
  
10. Объявите событие `SmartTagsChanged` .  
  
     [!code-csharp[VSSDKSmartTagTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#9)]
     [!code-vb[VSSDKSmartTagTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#9)]  
  
11. Реализуйте обработчик событий `OnLayoutChanged` для вызова события `TagsChanged`, которое приводит к вызову <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A>.  
  
     [!code-csharp[VSSDKSmartTagTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#10)]
     [!code-vb[VSSDKSmartTagTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#10)]  
  
12. Реализуйте метод <xref:System.IDisposable.Dispose%2A> так, чтобы он отменял подписку на событие <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>.  
  
     [!code-csharp[VSSDKSmartTagTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#11)]
     [!code-vb[VSSDKSmartTagTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#11)]  
  
## <a name="implementing-the-smart-tag-tagger-provider"></a>Реализация поставщика разметчика смарт-тегов  
  
#### <a name="to-implement-the-smart-tag-tagger-provider"></a>Реализация поставщика разметчика смарт-тегов  
  
1. Добавьте класс с именем `TestSmartTagTaggerProvider`, производный от <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>. Экспортируйте его с атрибутом <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> со значением text, атрибутом <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> со значением Before="default" и атрибутом <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> со значением <xref:Microsoft.VisualStudio.Language.Intellisense.SmartTag>.  
  
     [!code-csharp[VSSDKSmartTagTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#12)]
     [!code-vb[VSSDKSmartTagTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#12)]  
  
2. Импортируйте <xref:Microsoft.VisualStudio.Text.Operations.ITextStructureNavigatorSelectorService> как свойство.  
  
     [!code-csharp[VSSDKSmartTagTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#13)]
     [!code-vb[VSSDKSmartTagTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#13)]  
  
3. Выполните метод <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A>.  
  
     [!code-csharp[VSSDKSmartTagTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#14)]
     [!code-vb[VSSDKSmartTagTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#14)]  
  
## <a name="implementing-smart-tag-actions"></a>Реализация действий смарт-тега  
  
#### <a name="to-implement-smart-tag-actions"></a>Реализация действий смарт-тега  
  
1. Создайте два класса с именами `UpperCaseSmartTagAction` и `LowerCaseSmartTagAction`. В обоих классах реализован интерфейс <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagAction>.  
  
    [!code-csharp[VSSDKSmartTagTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#15)]
    [!code-vb[VSSDKSmartTagTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#15)]  
  
    [!code-csharp[VSSDKSmartTagTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#16)]
    [!code-vb[VSSDKSmartTagTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#16)]  
  
   Эти два класса похожи за тем исключением, что один из них вызывает <xref:System.String.ToUpper%2A>, а другой вызывает <xref:System.String.ToLower%2A>. В дальнейших шагах рассматривается создание класса для действия преобразования в верхний регистр, но вам необходимо реализовать оба класса. Используйте инструкции по реализации действия преобразования в верхний регистр в качестве шаблона для реализации действия преобразования в нижний регистр.  
  
2. Объявите набор закрытых полей.  
  
    [!code-csharp[VSSDKSmartTagTest#17](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#17)]
    [!code-vb[VSSDKSmartTagTest#17](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#17)]  
  
3. Добавьте конструктор, который задает поля.  
  
    [!code-csharp[VSSDKSmartTagTest#18](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#18)]
    [!code-vb[VSSDKSmartTagTest#18](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#18)]  
  
4. Реализуйте свойства указанным ниже образом.  
  
    [!code-csharp[VSSDKSmartTagTest#19](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#19)]
    [!code-vb[VSSDKSmartTagTest#19](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#19)]  
  
5. Реализуйте метод <xref:Microsoft.VisualStudio.Language.Intellisense.ISmartTagAction.Invoke%2A>, заменив текст в диапазоне на эквивалентный текст в верхнем регистре.  
  
    [!code-csharp[VSSDKSmartTagTest#20](../snippets/csharp/VS_Snippets_VSSDK/vssdksmarttagtest/cs/testsmarttag.cs#20)]
    [!code-vb[VSSDKSmartTagTest#20](../snippets/visualbasic/VS_Snippets_VSSDK/vssdksmarttagtest/vb/testsmarttag.vb#20)]  
  
## <a name="building-and-testing-the-code"></a>Сборка и тестирование кода  
 Чтобы проверить код, выполните сборку решения SmartTagTest и запустите его в экспериментальном экземпляре.  
  
#### <a name="to-build-and-test-the-smarttagtest-solution"></a>Сборка и тестирование решения SmartTagTest  
  
1. Создайте решение.  
  
2. При запуске этого проекта в отладчике создается второй экземпляр Visual Studio.  
  
3. Создайте текстовый файл и введите любой текст.  
  
     Первая буква в первом слове текста должна быть подчеркнута синей линией.  
  
4. Наведите указатель на синюю линию.  
  
     Рядом с указателем должна появиться кнопка.  
  
5. Если нажать кнопку, должны отобразиться два предлагаемых действия: **Преобразовать в верхний регистр** и **Преобразовать в нижний регистр**. Если выбрать первое действие, все символы текущего слова должны преобразоваться в верхний регистр. Если выбрать второе действие, все символы должны преобразоваться в нижний регистр.  
  
## <a name="see-also"></a>См. также:  
 [Пошаговое руководство. Связывание типа контента с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)
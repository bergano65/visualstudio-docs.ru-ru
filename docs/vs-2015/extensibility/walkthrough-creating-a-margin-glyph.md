---
title: Пошаговое руководство. Создание глифа поля | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - margin glyph
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: aa18b900ca44fbb52c646bfdf021beed6e77f504
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148848"
---
# <a name="walkthrough-creating-a-margin-glyph"></a>Пошаговое руководство. Создание глифа поля
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Внешний вид полей редактора можно настроить с помощью пользовательских расширений редактора. Это пошаговое руководство помещает пользовательский глиф на поле индикатора каждый раз, когда слово «TODO» появляется в комментарии к коду.  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Кроме того, пакет SDK для VS можно установить позже. Дополнительные сведения см. [в разделе Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Создание проекта MEF  
  
1. Создание проекта VSIX C#. (В диалоговом окне **Новый проект** выберите **Visual C#/Extensibility**, а затем **проект VSIX**.) Присвойте решению имя `TodoGlyphTest` .  
  
2. Добавьте элемент проекта классификатора редактора. Дополнительные сведения см. в разделе [Создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Удалите файлы существующих классов.  
  
## <a name="defining-the-glyph"></a>Определение глифа  
 Определите глиф, реализовав <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> интерфейс.  
  
#### <a name="to-define-the-glyph"></a>Определение глифа  
  
1. Добавьте файл класса с именем `TodoGlyphFactory`.  
  
2. Добавьте следующие объявления с помощью объявлений.  
  
     [!code-csharp[VSSDKTodoGlyphTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#1)]
     [!code-vb[VSSDKTodoGlyphTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#1)]  
  
3. Добавьте класс с именем `TodoGlyphFactory` , реализующий <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> .  
  
     [!code-csharp[VSSDKTodoGlyphTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#2)]
     [!code-vb[VSSDKTodoGlyphTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#2)]  
  
4. Добавьте закрытое поле, определяющее размеры глифа.  
  
     [!code-csharp[VSSDKTodoGlyphTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#3)]
     [!code-vb[VSSDKTodoGlyphTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#3)]  
  
5. Реализуйте `GenerateGlyph` , определив элемент пользовательского интерфейса глифа. `TodoTag` задается далее в этом пошаговом руководстве.  
  
     [!code-csharp[VSSDKTodoGlyphTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#4)]
     [!code-vb[VSSDKTodoGlyphTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#4)]  
  
6. Добавьте класс с именем `TodoGlyphFactoryProvider` , реализующий <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider> . Экспортируйте этот класс с помощью <xref:Microsoft.VisualStudio.Utilities.NameAttribute> "тодоглиф", объекта <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> после встекстмаркер, a <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> из "Code" и объекта <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> тодотаг.  
  
     [!code-csharp[VSSDKTodoGlyphTest#5](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#5)]
     [!code-vb[VSSDKTodoGlyphTest#5](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#5)]  
  
7. Реализуйте <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> метод, создав экземпляр `TodoGlyphFactory` .  
  
     [!code-csharp[VSSDKTodoGlyphTest#6](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todoglyphfactory.cs#6)]
     [!code-vb[VSSDKTodoGlyphTest#6](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todoglyphfactory.vb#6)]  
  
## <a name="defining-a-todo-tag-and-tagger"></a>Определение тега TODO и создания его тегов  
 Определите связь между элементом пользовательского интерфейса, который вы определили в предыдущих шагах, и полем индикатора, создав тип тега и средство создания тегов, а затем экспортировав его с помощью поставщика тегов.  
  
#### <a name="to-define-a-todo-tag-and-tagger"></a>Определение тега TODO и создания его тегов  
  
1. Добавьте в проект новый файл класса и присвойте ему имя `TodoTagger` .  
  
2. Добавьте приведенные ниже импортированные данные.  
  
     [!code-csharp[VSSDKTodoGlyphTest#7](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#7)]
     [!code-vb[VSSDKTodoGlyphTest#7](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#7)]  
  
3. Добавьте класс с именем `TodoTag`.  
  
     [!code-csharp[VSSDKTodoGlyphTest#8](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#8)]
     [!code-vb[VSSDKTodoGlyphTest#8](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#8)]  
  
4. Измените класс с именем `TodoTagger` , реализующий <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> тип `TodoTag` .  
  
     [!code-csharp[VSSDKTodoGlyphTest#9](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#9)]
     [!code-vb[VSSDKTodoGlyphTest#9](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#9)]  
  
5. К `TodoTagger` классу Добавьте закрытые поля для <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> и для текста, который необходимо найти в области классификации.  
  
     [!code-csharp[VSSDKTodoGlyphTest#10](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#10)]
     [!code-vb[VSSDKTodoGlyphTest#10](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#10)]  
  
6. Добавьте конструктор, который задает классификатор.  
  
     [!code-csharp[VSSDKTodoGlyphTest#11](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#11)]
     [!code-vb[VSSDKTodoGlyphTest#11](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#11)]  
  
7. Реализуйте <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> метод, находя все диапазоны классификации, имена которых содержат слово "Comment", а текст, содержащий искомый текст. При обнаружении искомого текста возвращает новый <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> тип `TodoTag` .  
  
     [!code-csharp[VSSDKTodoGlyphTest#12](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#12)]
     [!code-vb[VSSDKTodoGlyphTest#12](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#12)]  
  
8. Объявите `TagsChanged` событие.  
  
     [!code-csharp[VSSDKTodoGlyphTest#13](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#13)]
     [!code-vb[VSSDKTodoGlyphTest#13](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#13)]  
  
9. Добавьте класс с именем `TodoTaggerProvider` , реализующий <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider> , и экспортируйте его с помощью <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "Code" и <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> тодотаг.  
  
     [!code-csharp[VSSDKTodoGlyphTest#14](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#14)]
     [!code-vb[VSSDKTodoGlyphTest#14](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#14)]  
  
10. Импортируйте <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService> .  
  
     [!code-csharp[VSSDKTodoGlyphTest#15](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#15)]
     [!code-vb[VSSDKTodoGlyphTest#15](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#15)]  
  
11. Реализуйте <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> метод, создав экземпляр `TodoTagger` .  
  
     [!code-csharp[VSSDKTodoGlyphTest#16](../snippets/csharp/VS_Snippets_VSSDK/vssdktodoglyphtest/cs/todotagger.cs#16)]
     [!code-vb[VSSDKTodoGlyphTest#16](../snippets/visualbasic/VS_Snippets_VSSDK/vssdktodoglyphtest/vb/todotagger.vb#16)]  
  
## <a name="building-and-testing-the-code"></a>Сборка и тестирование кода  
 Чтобы протестировать этот код, создайте решение Тодоглифтест и запустите его в экспериментальном экземпляре.  
  
#### <a name="to-build-and-test-the-todoglyphtest-solution"></a>Создание и тестирование решения Тодоглифтест  
  
1. Создайте решение.  
  
2. Запустите проект, нажав клавишу F5. Создается второй экземпляр Visual Studio.  
  
3. Убедитесь, что поле индикатора отображается. (В меню **Сервис** выберите пункт **Параметры**. На странице **текстовый редактор** убедитесь, что **поле индикатор** выбрано.)  
  
4. Откройте файл кода с комментариями. Добавьте слово «TODO» в один из разделов комментариев.  
  
5. Светло-синий круг, имеющий темно-синий контур, должен появиться на поле индикатора слева от окна кода.

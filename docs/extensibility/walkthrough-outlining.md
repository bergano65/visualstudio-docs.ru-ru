---
title: 'Пошаговая прогулка: Изложение Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - outlining
ms.assetid: d75a44aa-265a-44d4-9c28-457f59c4ff9f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 97b9dcbb2a24f1a3ed336a4a6bb7de4a15e907b4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697211"
---
# <a name="walkthrough-outlining"></a>Пошаговое руководство. Структурирование
Настроите функции на основе языка, такие как описание, определяя виды текстовых областей, которые вы хотите расширить или свернуть. Можно определить регионы в контексте языковой службы, определить свое собственное расширение и тип содержимого имени файла и применить определение региона только к этому типу, или применить определения региона к существующему типу содержимого (например, "текст"). В этом пошаговом показании, как определить и отобразить области.

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, вы не устанавливаете Visual Studio SDK из центра загрузки. Он включен в качестве дополнительной функции в Visual Studio установки. Вы также можете установить VS SDK позже. Для получения дополнительной информации, [см.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Создание проекта управляемой расширительности (MEF)

### <a name="to-create-a-mef-project"></a>Создание проекта MEF

1. Создайте проект VSIX. Назовите решение `OutlineRegionTest`.

2. Добавьте шаблон элемента классификатора редактора в проект. Для получения дополнительной информации [см. Создать расширение с шаблоном элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Удалите файлы существующих классов.

## <a name="implement-an-outlining-tagger"></a>Реализация сизложенного тегетера
 Области с изложением отмечены<xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag>своего рода тегом (). Этот тег обеспечивает стандартное поведение с изложением. Обозначенный регион может быть расширен или разрушен. Обозначенный регион отмечен знаком Plus**+**(), если он рухнул или**-** знак Минус () если он расширен, а расширенный регион разграничен вертикальной линией.

 Следующие шаги показывают, как определить теггер, который создает области с изложением для всех регионов, делимитированных скобками **(**.**.**. . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . .

### <a name="to-implement-an-outlining-tagger"></a>Для реализации сметы с изложением

1. Добавьте файл класса с именем `OutliningTagger`.

2. Импортируйте следующие пространства имен.

     [!code-csharp[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/CSharp/walkthrough-outlining_1.cs)]
     [!code-vb[VSSDKOutlineRegionTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_1.vb)]

3. Создайте класс `OutliningTagger`под названием <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601>и реализуйте его:

     [!code-csharp[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/CSharp/walkthrough-outlining_2.cs)]
     [!code-vb[VSSDKOutlineRegionTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_2.vb)]

4. Добавьте несколько полей для отслеживания буфера текста и моментального снимка и накопления наборов строк, которые должны быть помечены как области с изложением. Этот код включает в себя список объектов Региона (которые будут определены позже), которые представляют области с изложением.

     [!code-csharp[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/CSharp/walkthrough-outlining_3.cs)]
     [!code-vb[VSSDKOutlineRegionTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_3.vb)]

5. Добавьте конструктор теге, который инициализирует поля, разбирает буфер <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> и добавляет обработчик события в событие.

     [!code-csharp[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/CSharp/walkthrough-outlining_4.cs)]
     [!code-vb[VSSDKOutlineRegionTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_4.vb)]

6. Реализация <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> метода, который мгновенно прокладывает теги. Этот пример предполагает, что пролеты в <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> пройдении метода являются смежными, хотя это не всегда так. Этот метод мгновенно устанавливает новый диапазон тегов для каждого из областей с изложением.

     [!code-csharp[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/CSharp/walkthrough-outlining_5.cs)]
     [!code-vb[VSSDKOutlineRegionTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_5.vb)]

7. Объявить `TagsChanged` обработчик анонса.

     [!code-csharp[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/CSharp/walkthrough-outlining_6.cs)]
     [!code-vb[VSSDKOutlineRegionTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_6.vb)]

8. Добавьте `BufferChanged` обработчик событий, который реагирует на <xref:Microsoft.VisualStudio.Text.ITextBuffer.Changed> события, разбирая текстовый буфер.

     [!code-csharp[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/CSharp/walkthrough-outlining_7.cs)]
     [!code-vb[VSSDKOutlineRegionTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_7.vb)]

9. Добавьте метод, который разбирает буфер. Приведенный здесь пример предназначен только для иллюстрации. Он синхронно разбирает буфер на вложенные области.

     [!code-csharp[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/CSharp/walkthrough-outlining_8.cs)]
     [!code-vb[VSSDKOutlineRegionTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_8.vb)]

10. Следующий метод помощника получает ряд, который представляет уровень изложения, таким образом, что 1 является левой пары скобки.

     [!code-csharp[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/CSharp/walkthrough-outlining_9.cs)]
     [!code-vb[VSSDKOutlineRegionTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_9.vb)]

11. Следующий метод помощника переводит регион (определяемый позже в этой статье) в SnapshotSpan.

     [!code-csharp[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/CSharp/walkthrough-outlining_10.cs)]
     [!code-vb[VSSDKOutlineRegionTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_10.vb)]

12. Следующий код предназначен только для иллюстрации. Он определяет класс PartialRegion, содержащий номер строки и смещение начала области с изложением, и ссылку на родительский регион (если таковой имеется). Этот код позволяет parser настроить вложенные области. Производный класс региона содержит ссылку на номер строки конца области.

     [!code-csharp[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/CSharp/walkthrough-outlining_11.cs)]
     [!code-vb[VSSDKOutlineRegionTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_11.vb)]

## <a name="implement-a-tagger-provider"></a>Реализация поставщика tagger
 Экспорт поставщика tagger для вашего tagger. Поставщик tagger создает `OutliningTagger` буфер типа содержимого "текст" или возвращает, `OutliningTagger` если буфер уже имеет его.

### <a name="to-implement-a-tagger-provider"></a>Для реализации поставщика tagger

1. Создайте класс, названный, `OutliningTaggerProvider` который <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>реализует, и экспортировать его с атрибутами ContentType и TagType.

     [!code-csharp[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/CSharp/walkthrough-outlining_12.cs)]
     [!code-vb[VSSDKOutlineRegionTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_12.vb)]

2. Реализация <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> метода путем добавления `OutliningTagger` в свойства буфера.

     [!code-csharp[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/CSharp/walkthrough-outlining_13.cs)]
     [!code-vb[VSSDKOutlineRegionTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-outlining_13.vb)]

## <a name="build-and-test-the-code"></a>Создание и тестирование кода
 Чтобы протестировать этот код, создайте решение OutlineRegionTest и запустите его в экспериментальном экземпляре.

### <a name="to-build-and-test-the-outlineregiontest-solution"></a>Создание и тестирование решения OutlineRegionTest

1. Создайте решение.

2. При запуске этого проекта в отладчике запускается второй экземпляр Visual Studio.

3. Создание текстового файла. Введите текст, который включает в себя как открывающиеся скобки, так и закрывающие скобки.

    ```
    [
       Hello
    ]
    ```

4. Должен быть спотыкающийся регион, который включает в себя обе скобки. Вы должны быть в состоянии нажать Минус знак слева от открытой кронштейна, чтобы свернуть область изложения. Когда область рухнула, символ эллипсиса *(...)* должен появиться слева от рухнувшей области, и всплывающее окно, содержащее **текст навистого** текста, должно появиться при перемещении указателя над эллипсисом.

## <a name="see-also"></a>См. также
- [Прохождение: Свяжите тип содержимого с расширением имени файла](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)

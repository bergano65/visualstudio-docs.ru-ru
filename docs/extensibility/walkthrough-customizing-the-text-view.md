---
title: Пошаговое руководство. Настройка представления текста | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fc0214ed8327354dc3662f039d33d032148f9437
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60083742"
---
# <a name="walkthrough-customize-the-text-view"></a>Пошаговое руководство. Настройка представления текста
Текстовое представление можно настроить путем изменения любого из следующих свойств в его формат редактор карты:

- Поле индикаторов

- Каретка вставки

- Перезаписать курсора

- Выделенный текст

- Неактивный выделенный текст (то есть выбранный текст, который потерял фокус)

- Видимый пробел

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, не следует устанавливать пакет SDK для Visual Studio из центра загрузки. Этот пакет включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установить пакет SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Создание проекта MEF

1. Создайте проект VSIX C#. (В **новый проект** диалоговом окне выберите **Visual C# / Extensibility**, затем **проект VSIX**.) Назовите решение `ViewPropertyTest`.

2. Добавьте в проект шаблон элемента классификатора редактора. Дополнительные сведения см. в разделе [создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Удалите файлы существующих классов.

## <a name="define-the-content-type"></a>Определить тип содержимого

1. Добавьте файл класса с именем `ViewPropertyModifier`.

2. Добавьте следующий `using` директивы:

    [!code-csharp[VSSDKViewPropertyTest#1](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs)]
    [!code-vb[VSSDKViewPropertyTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]

3. Объявите класс с именем `TestViewCreationListener` , наследуемый от <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>. Экспортируйте этот класс со следующими атрибутами:

   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> Чтобы указать тип содержимого, к которому применяется данный прослушиватель.

   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> для указания роли этого прослушивателя.

     [!code-csharp[VSSDKViewPropertyTest#2](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]

4. В этом классе импортировать <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>.

    [!code-csharp[VSSDKViewPropertyTest#3](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs)]
    [!code-vb[VSSDKViewPropertyTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]

## <a name="change-the-view-properties"></a>Изменение свойств представления

1. Настройка <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> метод таким образом, чтобы просмотреть свойства изменяются при открытии представления. Чтобы внести необходимые изменения, сначала найдите <xref:System.Windows.ResourceDictionary> , соответствующий аспектом представление, необходимо найти. Затем измените соответствующие свойства в словаре ресурсов и настройте свойства. Пакетная вызовы <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> , вызывая <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> метод, прежде чем указывать свойства и затем <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> после задания свойства.

     [!code-csharp[VSSDKViewPropertyTest#4](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs)]
     [!code-vb[VSSDKViewPropertyTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]

## <a name="build-and-test-the-code"></a>Построение и тестирование кода

1. Постройте решение.

     При запуске этого проекта в отладчике, запускается второй экземпляр Visual Studio.

2. Создайте текстовый файл и введите любой текст.

    - Курсор вставки должен быть пурпурный и перезаписать курсор должен быть бирюзовый.

    - Поле индикаторов (слева от представления текста) должен быть индикатор зеленый.

3. Выделите текст, который вы ввели. Цвет выделенного текста должно быть свет розовый.

4. Когда текст выбран, щелкните за пределами текстового окна. Цвет выделенного текста должно быть темно-розовый.

5. Включите видимый пробел. (На **изменить** последовательно выберите пункты **Дополнительно** и нажмите кнопку **Показать пустое пространство**). Введите некоторые вкладки в тексте. Красные стрелки, представляющие вкладки должны отображаться.

## <a name="see-also"></a>См. также
- [Точки расширения редактора и служба языка](../extensibility/language-service-and-editor-extension-points.md)
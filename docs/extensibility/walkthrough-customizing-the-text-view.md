---
title: 'Пошаговое: Настройка текстового представления Документы Майкрософт'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9d99f9201761bbe079c34ccf61339158863509dd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697458"
---
# <a name="walkthrough-customize-the-text-view"></a>Пошаговое: Настроить текстовое представление
Можно настроить текстовый вид, изменив любой из следующих свойств на карте формата редактора:

- Поле индикаторов

- Вставка уход

- Перезапись карет

- Выбранный текст

- Неактивный выбранный текст (т.е. выбранный текст, который потерял фокус)

- Видимое белое пространство

## <a name="prerequisites"></a>Предварительные требования
 Начиная с Visual Studio 2015, вы не устанавливаете Visual Studio SDK из центра загрузки. Он включен в качестве дополнительной функции в Visual Studio установки. Вы также можете установить VS SDK позже. Для получения дополнительной информации, [см.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-mef-project"></a>Создание проекта MEF

1. Создайте проект СЗ VSIX. (В **диалоге нового проекта** выберите **Visual C / Расширяемость,** затем **VSIX Project**.) Назовите решение. `ViewPropertyTest`

2. Добавьте шаблон элемента классификатора редактора в проект. Для получения дополнительной информации [см. Создать расширение с шаблоном элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Удалите файлы существующих классов.

## <a name="define-the-content-type"></a>Определение типа содержимого

1. Добавьте файл класса с именем `ViewPropertyModifier`.

2. Затем добавьте следующие `using` директивы:

    [!code-csharp[VSSDKViewPropertyTest#1](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs)]
    [!code-vb[VSSDKViewPropertyTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]

3. Объявить класс, названный, `TestViewCreationListener` который наследует от <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>. Экспортировать этот класс со следующими атрибутами:

   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>указать тип содержимого, к которому относится этот слушатель.

   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>определить роль этого слушателя.

     [!code-csharp[VSSDKViewPropertyTest#2](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]

4. В этом классе <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>импортируйте .

    [!code-csharp[VSSDKViewPropertyTest#3](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs)]
    [!code-vb[VSSDKViewPropertyTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]

## <a name="change-the-view-properties"></a>Изменение свойств представления

1. Настроили <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> метод таким образом, чтобы свойства представления изменялись при открытии представления. Чтобы внести изменения, <xref:System.Windows.ResourceDictionary> сначала найдите то, что соответствует аспекту представления, которое вы хотите найти. Затем измените соответствующее свойство в словаре ресурса и установите свойства. Вынаните <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> вызовы метода, вызовив <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> метод <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> перед установкой свойств, а затем после установки свойств.

     [!code-csharp[VSSDKViewPropertyTest#4](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs)]
     [!code-vb[VSSDKViewPropertyTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]

## <a name="build-and-test-the-code"></a>Создание и тестирование кода

1. Создайте решение.

     При запуске этого проекта в отладчике запускается второй экземпляр Visual Studio.

2. Создайте текстовый файл и введите любой текст.

    - Вставка уход должен быть пурпурным и перезаписать caret должны быть бирюзовыми.

    - Маржа индикатора (слева от текстового представления) должна быть светло-зеленой.

3. Выберите набранный текст. Цвет выбранного текста должен быть светло-розовым.

4. В то время как текст выбран, нажмите в любом месте за пределами текстового окна. Цвет выбранного текста должен быть темно-розовым.

5. Включите видимое белое пространство. (В меню **edit,** укажите на **Расширенный,** а затем нажмите **Просмотр Белого пространства**). Введите некоторые вкладки в тексте. Красные стрелки, представляющие вкладки, должны отображаться.

## <a name="see-also"></a>См. также
- [Языковой сервис и точки расширения редактора](../extensibility/language-service-and-editor-extension-points.md)

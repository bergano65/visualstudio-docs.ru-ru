---
title: Пошаговое руководство по настройке внешнего вида текста | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4fb4762a422102b91c44d755d387168ab0572f2a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31142086"
---
# <a name="walkthrough-customizing-the-text-view"></a>Пошаговое руководство: Настройка текстового представления.
Можно настроить представление текста с изменением любого из следующих свойств в его формат редактор карты:  
  
-   Поле индикаторов  
  
-   Каретка вставки  
  
-   Перезаписать курсора  
  
-   Выделенный текст  
  
-   Неактивный выделенный текст (то есть выделенный текст, потерял фокус)  
  
-   Видимый пробел  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки Майкрософт. Он включен в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Создание проекта MEF  
  
1.  Создайте проект VSIX C#. (В **новый проект** диалогового окна выберите **Visual C# / Extensibility**, затем **проект VSIX**.) Присвойте решению имя `ViewPropertyTest`.  
  
2.  Добавьте в проект шаблон элемента классификатора редактора. Дополнительные сведения см. в разделе [создания расширения с помощью шаблона элемента редактор](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Удалите файлы существующих классов.  
  
## <a name="defining-the-content-type"></a>Определение типа контента  
  
1.  Добавьте файл класса и назовите его `ViewPropertyModifier`.  
  
2.  Добавьте следующие `using` директивы:  
  
     [!code-csharp[VSSDKViewPropertyTest#1](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs)]
     [!code-vb[VSSDKViewPropertyTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]  
  
3.  Объявите класс с именем `TestViewCreationListener` , наследуемый от <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>. Экспортируйте класс со следующими атрибутами:  
  
    -   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> Чтобы указать тип содержимого, к которому применяется данный прослушиватель.  
  
    -   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> Чтобы указать роль этого прослушивателя.  
  
     [!code-csharp[VSSDKViewPropertyTest#2](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]  
  
4.  В этом классе импорта <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>.  
  
     [!code-csharp[VSSDKViewPropertyTest#3](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs)]
     [!code-vb[VSSDKViewPropertyTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]  
  
## <a name="changing-the-view-properties"></a>Изменение свойств представления  
  
1.  Реализуйте <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> метод, чтобы просмотреть свойства изменяются при открытии представления. Чтобы внести необходимые изменения, сначала найдите <xref:System.Windows.ResourceDictionary> , соответствующий аспект нужное представление. Затем измените соответствующие свойства в словаре ресурсов и задайте свойства. Пакетное вызовы <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> метод путем вызова <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> метод перед заданием свойств и затем <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> после задания свойства.  
  
     [!code-csharp[VSSDKViewPropertyTest#4](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs)]
     [!code-vb[VSSDKViewPropertyTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]  
  
## <a name="building-and-testing-the-code"></a>Сборка и тестирование кода  
  
1.  Постройте решение.  
  
     При запуске этого проекта в отладчике создается второй экземпляр Visual Studio.  
  
2.  Создайте текстовый файл и введите любой текст.  
  
    -   Каретка вставки должен быть magenta и перезаписать курсор должен быть бирюзовым цветом.  
  
    -   Поле индикаторов (слева от текстового представления) должен быть светлым зеленый.  
  
3.  Выберите только что введенный текст. Цвет выбранного текста должен быть светлым розовым цветом.  
  
4.  Пока выбран текст, щелкните за пределами текстового окна. Цвет выделенного текста необходимо темной розовый цвет.  
  
5.  Включите видимый пробел. (На **изменить** последовательно выберите пункты **Дополнительно** и нажмите кнопку **показывать пробелы**). Введите текст некоторые вкладки. Красные стрелки, которые представляют вкладки должны отображаться.  
  
## <a name="see-also"></a>См. также  
 [Языковая служба и точки расширения редактора](../extensibility/language-service-and-editor-extension-points.md)
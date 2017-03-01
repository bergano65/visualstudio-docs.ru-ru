---
title: "Пошаговое руководство: Настройка представления текста | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
caps.latest.revision: 22
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: e40368ed6aaf68b747f19cffe4e378a89ff6c0b5
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-customizing-the-text-view"></a>Пошаговое руководство: Настройка представления текста
Текстовое представление можно настроить, изменив следующие свойства в формате редактор карты:  
  
-   Поле индикаторов  
  
-   Курсор вставки  
  
-   Перезаписать курсора  
  
-   Выделенный текст  
  
-   Неактивный выделенный текст (то есть, выбранный текст, который потерял фокус)  
  
-   Видимый пробел  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не установить пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в установку Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Создание проекта MEF  
  
1.  Создайте проект VSIX C#. (В **новый проект** диалогового окна выберите **Visual C# и расширяемость**, затем **проект VSIX**.) Присвойте решению имя `ViewPropertyTest`.  
  
2.  Добавьте в проект шаблон элемента редактор классификатора. Дополнительные сведения см. в разделе [создания расширения с помощью редактора шаблона элемента](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Удалите файлы существующих классов.  
  
## <a name="defining-the-content-type"></a>Определение типа содержимого  
  
1.  Добавьте файл класса с именем `ViewPropertyModifier`.  
  
2.  Добавьте следующие `using` директивы:  
  
     [!code-cs[#1 VSSDKViewPropertyTest](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_1.cs) ] 
     [!code-vb [VSSDKViewPropertyTest&#1;](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_1.vb)]  
  
3.  Объявите класс с именем `TestViewCreationListener` , производный от <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>.</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> Экспортируйте класс со следующими атрибутами:  
  
    -   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>Чтобы указать тип содержимого, к которому применяется данный прослушиватель.</xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>  
  
    -   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>Чтобы указать роль этого прослушивателя.</xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute>  
  
     [!code-cs[VSSDKViewPropertyTest&2;](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_2.cs)]
     [!code-vb[VSSDKViewPropertyTest&#2;](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_2.vb)]  
  
4.  В этом классе импорта <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>.</xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>  
  
     [!code-cs[VSSDKViewPropertyTest&3;](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_3.cs) ] 
     [!code-vb [VSSDKViewPropertyTest&#3;](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_3.vb)]  
  
## <a name="changing-the-view-properties"></a>Изменение свойств представления  
  
1.  Реализация <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A>метода, чтобы просмотреть свойства изменяются при открытии представления.</xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> Чтобы внести необходимые изменения, найти <xref:System.Windows.ResourceDictionary>, соответствующий аспект нужное представление.</xref:System.Windows.ResourceDictionary> Затем измените соответствующие свойства в словаре ресурсов и задать свойства. Пакет вызовы <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A>, вызывая <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A>метод перед заданием свойства и затем <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A>После настройки свойств.</xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> </xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> </xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A>  
  
     [!code-cs[#4 VSSDKViewPropertyTest](../extensibility/codesnippet/CSharp/walkthrough-customizing-the-text-view_4.cs) ] 
     [!code-vb [VSSDKViewPropertyTest&#4;](../extensibility/codesnippet/VisualBasic/walkthrough-customizing-the-text-view_4.vb)]  
  
## <a name="building-and-testing-the-code"></a>Сборка и тестирование кода  
  
1.  Постройте решение.  
  
     При запуске этого проекта в отладчике создается второй экземпляр Visual Studio.  
  
2.  Создайте текстовый файл и введите любой текст.  
  
    -   Курсор вставки должен быть пурпурный и перезаписать курсор должен быть бирюзовый.  
  
    -   Поле индикаторов (слева от представления текста) должен быть свет зеленый.  
  
3.  Выберите только что введенный текст. Цвет выбранного текста должен быть свет розовый.  
  
4.  Хотя текст выбран, щелкните за пределами текстового окна. Цвет выбранного текста следует темно-розовый.  
  
5.  Включите видимый пробел. (На **изменить** наведите указатель мыши на **Дополнительно** и нажмите кнопку **показывать пробелы**). Введите текст некоторые вкладки. Красные стрелки, представляющие вкладки должны отображаться.  
  
## <a name="see-also"></a>См. также  
 [Служба языка и точек расширения редактора](../extensibility/language-service-and-editor-extension-points.md)

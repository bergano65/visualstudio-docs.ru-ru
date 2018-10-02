---
title: 'Пошаговое руководство: Настройка представления текста | Документация Майкрософт'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
caps.latest.revision: 23
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 39dca1309adeef8270ae7bb716c4274874451b91
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47559962"
---
# <a name="walkthrough-customizing-the-text-view"></a>Пошаговое руководство. Настройка представления текста
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [Пошаговое руководство: Настройка представления текста](https://docs.microsoft.com/visualstudio/extensibility/walkthrough-customizing-the-text-view).  
  
Текстовое представление можно настроить путем изменения любого из следующих свойств в его формат редактор карты:  
  
-   Поле индикаторов  
  
-   Каретка вставки  
  
-   Перезаписать курсора  
  
-   Выделенный текст  
  
-   Неактивный выделенный текст (то есть выбранный текст, который потерял фокус)  
  
-   Видимый пробел  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, не следует устанавливать пакет SDK для Visual Studio из центра загрузки. Она будет включена в качестве дополнительного компонента в программе установки Visual Studio. VS SDK также можно установить позже. Дополнительные сведения см. в разделе [установка Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Создание проекта MEF  
  
1.  Создайте проект VSIX C#. (В **новый проект** диалоговом окне выберите **Visual C# / Extensibility**, затем **проект VSIX**.) Назовите решение `ViewPropertyTest`.  
  
2.  Добавьте в проект шаблон элемента классификатора редактора. Дополнительные сведения см. в разделе [создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Удалите файлы существующих классов.  
  
## <a name="defining-the-content-type"></a>Определение типа содержимого  
  
1.  Добавьте файл класса и назовите его `ViewPropertyModifier`.  
  
2.  Добавьте следующий `using` директивы:  
  
     [!code-csharp[VSSDKViewPropertyTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#1)]
     [!code-vb[VSSDKViewPropertyTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#1)]  
  
3.  Объявите класс с именем `TestViewCreationListener` , наследуемый от <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener>. Экспортируйте этот класс со следующими атрибутами:  
  
    -   <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> Чтобы указать тип содержимого, к которому применяется данный прослушиватель.  
  
    -   <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> для указания роли этого прослушивателя.  
  
     [!code-csharp[VSSDKViewPropertyTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#2)]
     [!code-vb[VSSDKViewPropertyTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#2)]  
  
4.  В этом классе импортировать <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService>.  
  
     [!code-csharp[VSSDKViewPropertyTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#3)]
     [!code-vb[VSSDKViewPropertyTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#3)]  
  
## <a name="changing-the-view-properties"></a>Изменение свойств представления  
  
1.  Реализуйте <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> метод таким образом, чтобы просмотреть свойства изменяются при открытии представления. Чтобы внести необходимые изменения, сначала найдите <xref:System.Windows.ResourceDictionary> , соответствующий аспектом представление, необходимо найти. Затем измените соответствующие свойства в словаре ресурсов и задать свойства. Пакетная вызовы <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> , вызывая <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> метод, прежде чем указывать свойства и затем <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> после задания свойства.  
  
     [!code-csharp[VSSDKViewPropertyTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#4)]
     [!code-vb[VSSDKViewPropertyTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#4)]  
  
## <a name="building-and-testing-the-code"></a>Сборка и тестирование кода  
  
1.  Постройте решение.  
  
     При запуске этого проекта в отладчике создается второй экземпляр Visual Studio.  
  
2.  Создайте текстовый файл и введите любой текст.  
  
    -   Курсор вставки должен быть пурпурный и перезаписать курсор должен быть бирюзовый.  
  
    -   Поле индикаторов (слева от представления текста) должен быть индикатор зеленый.  
  
3.  Выберите только что введенный текст. Цвет выделенного текста должно быть свет розовый.  
  
4.  Когда текст выбран, щелкните за пределами текстового окна. Цвет выделенного текста должно быть темно-розовый.  
  
5.  Включите видимый пробел. (На **изменить** последовательно выберите пункты **Дополнительно** и нажмите кнопку **Показать пустое пространство**). Введите некоторые вкладки в тексте. Красные стрелки, представляющие вкладки должны отображаться.  
  
## <a name="see-also"></a>См. также  
 [Языковая служба и точки расширения редактора](../extensibility/language-service-and-editor-extension-points.md)


---
title: Пошаговое руководство. Настройка представления текста | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e96bb177d3cfa90b2c80304eabfd93d1bea76d5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202022"
---
# <a name="walkthrough-customizing-the-text-view"></a>Пошаговое руководство. Настройка представления текста
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Можно настроить представление текста, изменив любое из следующих свойств в его сопоставлении в формате редактора:  
  
- Поле индикаторов  
  
- Курсор вставки  
  
- Перезаписать курсор  
  
- Выделенный текст  
  
- Неактивный выделенный текст (т. е. выбранный текст, который потерял фокус)  
  
- Видимый пробел  
  
## <a name="prerequisites"></a>Предварительные требования  
 Начиная с Visual Studio 2015, пакет SDK для Visual Studio не устанавливается из центра загрузки. Он входит в состав программы установки Visual Studio как дополнительный компонент. Кроме того, пакет SDK для VS можно установить позже. Дополнительные сведения см. [в разделе Установка пакета SDK для Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Создание проекта MEF  
  
1. Создание проекта VSIX C#. (В диалоговом окне **Новый проект** выберите **Visual C#/Extensibility**, а затем **проект VSIX**.) Присвойте решению имя `ViewPropertyTest` .  
  
2. Добавьте шаблон элемента классификатора редактора в проект. Дополнительные сведения см. в разделе [Создание расширения с помощью шаблона элемента редактора](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Удалите файлы существующих классов.  
  
## <a name="defining-the-content-type"></a>Определение типа содержимого  
  
1. Добавьте файл класса с именем `ViewPropertyModifier`.  
  
2. Затем добавьте следующие `using` директивы:  
  
    [!code-csharp[VSSDKViewPropertyTest#1](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#1)]
    [!code-vb[VSSDKViewPropertyTest#1](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#1)]  
  
3. Объявите класс с именем `TestViewCreationListener` , наследуемый от <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> . Экспортируйте этот класс со следующими атрибутами:  
  
   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> для указания типа содержимого, к которому применяется этот прослушиватель.  
  
   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> для указания роли этого прослушивателя.  
  
     [!code-csharp[VSSDKViewPropertyTest#2](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#2)]
     [!code-vb[VSSDKViewPropertyTest#2](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#2)]  
  
4. В этом классе импортируйте <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService> .  
  
    [!code-csharp[VSSDKViewPropertyTest#3](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#3)]
    [!code-vb[VSSDKViewPropertyTest#3](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#3)]  
  
## <a name="changing-the-view-properties"></a>Изменение свойств представления  
  
1. Реализуйте <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> метод таким образом, чтобы свойства представления изменялись при открытии представления. Чтобы внести изменения, сначала найдите объект <xref:System.Windows.ResourceDictionary> , соответствующий аспекту представления, которое необходимо найти. Затем измените соответствующее свойство в словаре ресурсов и задайте свойства. Выполните пакетную обработку вызовов <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> метода, вызвав <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> метод до задания свойств, а затем <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> после установки свойств.  
  
     [!code-csharp[VSSDKViewPropertyTest#4](../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs#4)]
     [!code-vb[VSSDKViewPropertyTest#4](../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb#4)]  
  
## <a name="building-and-testing-the-code"></a>Сборка и тестирование кода  
  
1. Создайте решение.  
  
     При запуске этого проекта в отладчике создается второй экземпляр Visual Studio.  
  
2. Создайте текстовый файл и введите любой текст.  
  
    - Курсор вставки должен быть пурпурным, а курсор перезаписи должен быть бирюзовым.  
  
    - Поле индикатора (слева от текстового представления) должно быть светло-зеленым.  
  
3. Выделите только что введенный текст. Цвет выделенного текста должен быть светло-розовый.  
  
4. Пока текст выбран, щелкните в любом месте за пределами текстового окна. Цвет выделенного текста должен быть темно-розовым.  
  
5. Включите видимый пробел. (В меню **Правка** наведите указатель на пункт **Дополнительно** и выберите пункт **Показать пустое пространство**). Введите в текст некоторые вкладки. Должны отобразиться красные стрелки, представляющие вкладки.  
  
## <a name="see-also"></a>См. также:  
 [Языковая служба и точки расширения редактора](../extensibility/language-service-and-editor-extension-points.md)

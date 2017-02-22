---
title: "Сведения о параметрах в языковую службу для прежних версий | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "языковые службы, метод советы"
  - "метод советы"
  - "языковые службы, параметр info подсказки"
  - "Интерфейс IVsMethodData"
  - "Сведения о параметре (технология IntelliSense)"
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Сведения о параметрах в языковую службу для прежних версий
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Подсказка о параметрах IntelliSense предоставляет пользователям подсказки, где они находятся в языковой конструкции.  
  
 Устаревший языковые службы реализуются как частью VSPackage, но это использование расширений MEF новый способ реализации возможностей службы языка. Для получения дополнительных см [Расширение редактора и языковые службы](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API как можно быстрее. Это улучшает производительность службы языка и позволяют воспользоваться преимуществами новых функций редактора.  
  
## Как работает параметр отображение кратких сведений  
 При вводе инструкции в редакторе VSPackage отображает окно небольшой всплывающей подсказки, содержащий определение оператора, вводимый. Например, если ввести инструкцию Microsoft Foundation Classes \(MFC\) \(например, `pMainFrame ->UpdateWindow`\) и нажмите клавишу открывающей скобки для начала перечисления параметров, появится подсказка метод Отображение определения `UpdateWindow` метод.  
  
 Отображение кратких сведений параметр обычно используются в сочетании с завершения операторов. Они наиболее полезны для языков, имеющих параметры или других отформатированную информацию после имени метода или ключевое слово.  
  
 Сведения о параметрах подсказки инициируются языковой службы за счет перехвата команды. Для перехвата символов пользователя, необходимо реализовать объект языковой службы <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейса и передать указатель на текстовое представление вашей <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> реализацию, путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> метод в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> интерфейса. Фильтр команды перехватывает команды, вводимые в окне кода. Отслеживать сведения о командах, чтобы определить, когда необходимо отобразить сведения о параметрах для пользователя. Можно использовать один и тот же фильтр команды для завершения операторов, маркеры ошибок и т. д.  
  
 При вводе ключевых слов, для которого языковая служба может предоставить подсказки языковая служба создает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> объекте и вызывает метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> метод в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> интерфейс IDE, чтобы отобразить подсказку уведомления. Создание <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> с помощью `VSLocalCreateInstance` и указав компонентного класса `CLSID_VsMethodTipWindow`.`VsLocalCreateInstance` является функцией, определяемой в vsdoc.h файл заголовка, который вызывает `QueryService` для локального реестра и вызывает `CreateInstance` для данного объекта для `CLSID_VsMethodTipWindow`.  
  
## Предоставляя Совет метода  
 Чтобы предоставить метод совет, вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> метод в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> интерфейса, передавая ему реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> интерфейса.  
  
 Если ваш <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> вызывается классом, его методы вызываются в следующем порядке:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>  
  
     Возвращает позицию и длину релевантных данных в настоящий момент буфер текста. Это указывает, что интегрированная среда разработки не затруднять данным по окна всплывающей подсказки.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>  
  
     Возвращает метод \(отсчитываемый от нуля индекс\) для первоначального отображения. Например если возвращается нуль, затем первый перегруженный метод изначально окно.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>  
  
     Возвращает число перегруженных методов, применимых в текущем контексте. Если возвращается значение больше 1 для этого метода, затем текстовое представление отображает стрелки вверх и вниз для вас. Если нажать кнопку со стрелкой вниз, IDE вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> метод. Если нажать кнопку со стрелкой вверх, IDE вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> метод.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>  
  
     Текст подсказки о параметрах будет создан во время несколько вызовов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> методы.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>  
  
     Возвращает количество параметров для отображения в методе.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>  
  
     Если возвращается метод число, соответствующее перегрузки, которые необходимо отобразить, этот метод вызывается, следуют вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> метод.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>  
  
     Сообщает службе языка для обновления редактора при отображении Совет метода. В <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> метод, выполните приведенный ниже код:  
  
    ```  
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).  
    ```  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>  
  
     Получение вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> метод при закрытии окна подсказки метод.
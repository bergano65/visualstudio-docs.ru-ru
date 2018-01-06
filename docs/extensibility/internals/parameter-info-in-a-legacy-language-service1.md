---
title: "Сведения о параметрах в прежних версий языка Service1 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services, method tips
- method tips
- language services, parameter info tooltip
- IVsMethodData interface
- Parameter Info (IntelliSense)
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 70f6a24a8d5a3d516286efe01cffc6e1d3514e18
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Сведения о параметрах в языковую службу прежних версий
Подсказка о параметрах IntelliSense предоставляет пользователям подсказки, где они находятся в конструкция языка.  
  
 Прежних версий языка службы реализованы как часть пакета VSPackage, но новой реализации возможностей службы языка можно выполнить с помощью расширений MEF. Подробнее см. в разделе [расширение редактора и языковые службы](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API, как можно быстрее. Это повысит быстродействие языковой службы и позволяют воспользоваться преимуществами новых функций редактора.  
  
## <a name="how-parameter-info-tooltips-work"></a>Как работают параметра Отображение кратких сведений  
 При вводе инструкцию в редакторе VSPackage отображает окно небольшой всплывающей подсказки, содержащий определение оператора, вводимый. Например, если инструкция Microsoft Foundation Classes (MFC) (такие как `pMainFrame ->UpdateWindow`) и нажмите клавишу открывающей скобки, чтобы начать со списком параметров, появляется подсказка метод Отображение определения `UpdateWindow` метод.  
  
 Отображение кратких сведений параметр обычно используются в сочетании с завершением операторов. Они полезны для языков, которые имеют параметры или другие форматированные данные после имени метода или ключевое слово.  
  
 Отображение кратких сведений параметр инициируются языковой службы за счет перехвата команды. Для перехвата пользователя символов, должен реализовывать объект языковой службы <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейса и передать указатель для представления текста вашей <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> реализацию путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> метод в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> интерфейса. Команда фильтр перехватывает команды, вводимые в окне кода. Мониторинг сведений о команде о том, когда для отображения сведений о параметрах для пользователя. Можно использовать один и тот же фильтр команды для завершения операторов, маркеры ошибок и т. д.  
  
 При вводе ключевого слова, для которого языковая служба может предоставить подсказки языковая служба создаст <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> и вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> метод в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> интерфейс уведомления IDE, чтобы отобразить подсказку. Создание <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> с помощью `VSLocalCreateInstance` и указав компонентного класса `CLSID_VsMethodTipWindow`. `VsLocalCreateInstance`является функцией, определяемой в vsdoc.h файла заголовка, который вызывает `QueryService` для локального реестра и вызовы `CreateInstance` на этот объект для `CLSID_VsMethodTipWindow`.  
  
## <a name="providing-a-method-tip"></a>Предоставление метода совет  
 Чтобы предоставить метод совет, вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> метод в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> интерфейс, передав его реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> интерфейса.  
  
 Если ваш <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> вызывается класса, его методы вызываются в следующем порядке:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>  
  
     Возвращает позицию и длину релевантных данных текущего буфера текста. Это заставляет IDE, чтобы не скрывать эти данные с помощью окна всплывающей подсказки.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>  
  
     Возвращает метод (отсчитываемый от нуля индекс) для первоначального отображения. Например если возвращается ноль, затем первый перегруженный метод изначально окно.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>  
  
     Возвращает количество перегруженные методы, которые применяются в текущем контексте. Если возвращает значение больше 1 для этого метода, то текстовое представление отображает стрелки вверх и вниз для вас. Если щелкнуть стрелку вниз, интегрированной среды разработки вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> метод. Если нажать кнопку со стрелкой вверх, интегрированной среды разработки вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> метод.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>  
  
     Текст всплывающей подсказки о параметрах будет создан во время несколько вызовов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> методы.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>  
  
     Возвращает количество параметров для отображения в методе.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>  
  
     Если возвращается метод число, соответствующее с перегрузкой должен отображаться данный метод вызывается, следуют вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> метод.  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>  
  
     Сообщает службе языка, чтобы обновить редактора, когда подсказка метод отображается. В <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> метода, вызвать следующий:  
  
    ```  
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).  
    ```  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>  
  
     Получать вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> метод при закрытии окна подсказки метода.
---
title: Сведения о параметрах в языковой службы прежних версий1 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, method tips
- method tips
- language services, parameter info tooltip
- IVsMethodData interface
- Parameter Info (IntelliSense)
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 93283854760c4ab8309d3769550beb664c14f41b
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66314653"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Сведения о параметрах в языковой службе прежних версий
Подсказка о параметрах IntelliSense предоставляет пользователям указания о где они находятся в конструкции языка.

 Устаревший языковой службы реализуются как часть пакета VSPackage, но новый способ реализовать функции языковой службы является использование расширений MEF. Дополнительные сведения см. в разделе [расширение редактора и языковых служб](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Мы рекомендуем начать использовать новый редактор API как можно скорее. Это улучшит производительность службы языка и позволяют воспользоваться преимуществами новых функций редактора.

## <a name="how-parameter-info-tooltips-work"></a>Как работают параметр отображение кратких сведений
 При вводе инструкцию в редакторе VSPackage отображается небольшой подсказки окно, содержащее определение оператора ввода. Например, если ввести инструкцию Microsoft Foundation Classes (MFC) (такие как `pMainFrame ->UpdateWindow`) и нажмите клавишу открывающей скобки, чтобы начать со списком параметров, отображается подсказка метода Отображение определения `UpdateWindow` метод.

 Отображение кратких сведений параметров обычно используются в сочетании с завершение операторов. Они наиболее полезны для языков, которые имеют параметры или других отформатированную информацию, после имени метода или ключевое слово.

 Сведения о параметрах подсказки инициируются через перехват команд языковой службы. Для перехвата пользователя символов, должен реализовывать объект службы языка <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс и передать указатель на представление текста вашей <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> реализации, путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> метод в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> интерфейс. Фильтр команды перехватывает команды, вводимые в окне кода. Мониторинг сведений о команде о том, когда для отображения сведений о параметрах для пользователя. Можно использовать один и тот же фильтр команды для завершения операторов, маркеры ошибок и т. д.

 При вводе ключевого слова, для которого языковая служба может предоставить подсказки языковая служба создаст <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> и вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> метод в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> интерфейса для уведомления IDE, чтобы отобразить подсказку. Создание <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> с помощью `VSLocalCreateInstance` и указав компонентного класса `CLSID_VsMethodTipWindow`. `VsLocalCreateInstance` — Это функция, определенная в vsdoc.h файл заголовка, который вызывает `QueryService` для локального реестра и вызывает `CreateInstance` для данного объекта для `CLSID_VsMethodTipWindow`.

## <a name="providing-a-method-tip"></a>Предоставляет подсказку метода
 Чтобы предоставить подсказку метода, вызвать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> метод в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> интерфейса, передавая ему реализации <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> интерфейс.

 Если ваш <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> вызывается класс, его методы вызываются в следующем порядке:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>

     Возвращает положение и длину релевантных данных текущего буфера текста. Это указывает, что интегрированная среда разработки, чтобы не скрывать эти данные с помощью окна всплывающей подсказки.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>

     Возвращает номер метода (отсчитываемый от нуля индекс), вы должны отображаться изначально. Например если возвращается ноль, затем первый перегруженный метод, изначально отображаемого.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>

     Возвращает число перегруженных методов, которые можно использовать в текущем контексте. Если возвращается значение больше 1 для этого метода, затем представление текста отображает стрелки вверх и вниз для вас. Если щелкнуть стрелку вниз, интегрированной среды разработки вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> метод. Если щелкнуть стрелку вверх, интегрированной среды разработки вызывает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> метод.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>

     Текст подсказки о параметрах создается во время несколько вызовов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> методы.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>

     Возвращает число параметров для отображения в методе.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>

     Если возвращается метод число, соответствующее перегрузки, которые необходимо отобразить, этот метод вызывается, а затем с помощью вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> метод.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>

     Сообщает службе языка для обновления редактора, когда отображается подсказка метода. В <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> метод, приведенный ниже код:

    ```
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).
    ```

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>

     Вы получите вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> метод при закрытии окна подсказки метода.
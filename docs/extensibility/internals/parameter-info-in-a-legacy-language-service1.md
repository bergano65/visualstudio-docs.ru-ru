---
title: Информация о параметрах в Справочнике Наследия1 (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, method tips
- method tips
- language services, parameter info tooltip
- IVsMethodData interface
- Parameter Info (IntelliSense)
ms.assetid: f367295e-45b6-45d2-9ec8-77481743beef
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c26073252aae5434ba5a8197955948d0d9ec883d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706800"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Сведения о параметрах в языковой службе прежних версий
Инструмент IntelliSense Parameter Info предоставляет пользователям подсказки о том, где они находятся в языковой конструкции.

 Устаревшие языковые службы реализуются как часть VSPackage, но новый способ реализации функций языкового сервиса заключается в использовании расширений MEF. Чтобы узнать больше, смотрите [Расширение редактора и языковых служб](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Мы рекомендуем вам начать использовать новый API редактора как можно скорее. Это повысит производительность вашего языкового сервиса и позволит вам воспользоваться новыми функциями редактора.

## <a name="how-parameter-info-tooltips-work"></a>Как параметр Информация Tooltips работы
 При вводе оператора в редакторе VSPackage отображает небольшое окно tooltip, содержащее определение набранной оператора. Например, если вы введете заявление Microsoft Foundation `pMainFrame ->UpdateWindow`Classes (MFC) (например), и нажмите клавишу открытия скобки, `UpdateWindow` чтобы начать перечисление параметров, появляется наконечник метода, отображающий определение метода.

 Параметр Инфо инструменты, как правило, используются в сочетании с завершением оператора. Они наиболее полезны для языков с параметрами или другой отформатированной информацией после названия метода или ключевого слова.

 Панели инструментов Parameter Info инициируются языковой службой посредством перехвата команд. Чтобы перехватить символы пользователей, объект <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> языковой службы должен реализовать <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> интерфейс и передать <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> текстовое <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> представление указателем на реализацию, позвонив по методу в интерфейсе. Командный фильтр перехватывает команды, которые вы вводите в окне кода. Мониторинг информации о команде, чтобы знать, когда отобразить информацию о параметрах пользователю. Вы можете использовать тот же командный фильтр для завершения оператора, маркеров ошибок и так далее.

 При вводе ключевого слова, для которого языковая служба может <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> предоставить <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> подсказки, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> то языковая служба создает объект и вызывает метод в интерфейсе, чтобы уведомить IDE для отображения подсказки. Создайте <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> объект `VSLocalCreateInstance` с помощью `CLSID_VsMethodTipWindow`и указания кокласса. `VsLocalCreateInstance`— функция, определяемая в файле `QueryService` заголовка vsdoc.h, которая требует локального реестра и вызывает `CreateInstance` этот объект для `CLSID_VsMethodTipWindow`.

## <a name="providing-a-method-tip"></a>Предоставление метода Совет
 Чтобы предоставить наконечник метода, позвоните методу <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> интерфейс, передав ему реализацию интерфейса.

 При <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> вызове класса его методы называются в следующем порядке:

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetContextStream%2A>

     Возвращает положение и длину соответствующих данных в текущем буфере текста. Это поручает IDE не скрывать эти данные с помощью окна tooltip.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetCurMethod%2A>

     Возвращает номер метода (нулевой индекс), который необходимо отобразить изначально. Например, если вы возвращаете ноль, то сначала представлен первый перегруженный метод.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetOverloadCount%2A>

     Возвращает количество перегруженных методов, применимых в текущем контексте. Если вы вернете значение больше 1 для этого метода, то текстовое представление отображает стрелки вверх и вниз для вас. При нажатии на стрелку вниз, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.NextMethod%2A> IDE вызывает метод. При нажатии на стрелку вверх, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.PrevMethod%2A> IDE вызывает метод.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A>

     Текст инструментария Parameter Info построен во время <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetMethodText%2A> нескольких <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A> вызовов к методам.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterCount%2A>

     Возвращает количество параметров для отображения в методе.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.GetParameterText%2A>

     Если вы возвращаете номер метода, соответствующий перегрузке, которую вы <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> хотите отобразить, этот метод вызывается с последующим вызовом к методу.

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A>

     Информирует языковую службу об обновлении редактора при отображении наконечника метода. В <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.UpdateView%2A> методе позвоните по следующему:

    ```
    <pTxWin> ->UpdateTipWindow(<pTip>, UTW_CONTENTCHANGED | UTW_CONTEXTCHANGED).
    ```

- <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>

     При закрытии окна <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> наконечника метода вы получаете вызов к методу.

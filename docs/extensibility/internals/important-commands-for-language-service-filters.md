---
title: Важные команды для фильтров языковой службы | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d0e2e605a0725c2f88922d3e3ce899263171bc4d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726932"
---
# <a name="important-commands-for-language-service-filters"></a>Важные команды для фильтров языковой службы
Если вы хотите создать полнофункциональный фильтр языковой службы, рассмотрите возможность обработки следующих команд. Полный список идентификаторов команд определяется в перечислении <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> для управляемого кода и в файле заголовка Стдидкмд. h для неуправляемого [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] кода. Файл Стдидкмд. h можно найти в *пути установки Visual Studio SDK*\висуалстудиоинтегратион\коммон\инк.

## <a name="commands-to-handle"></a>Команды для обработки

> [!NOTE]
> Фильтрация для каждой команды в следующей таблице необязательна.

|Команда|Описание|
|-------------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Посылается, когда пользователь щелкает правой кнопкой мыши. Эта команда указывает, что пора указать контекстное меню. Если эта команда не обрабатывается, текстовый редактор предоставляет контекстное меню по умолчанию без каких-либо команд, зависящих от языка. Чтобы включить в это меню собственные команды, обработайте команду и откройте контекстное меню самостоятельно.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Обычно отправляется, когда пользователь вводит CTRL + J. Вызовите метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>, чтобы отобразить поле завершения инструкции.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Посылается, когда пользователь вводит символ. Отслеживайте эту команду, чтобы определить, когда был введен символ триггера и что необходимо для завершения операторов, советов по методам и текстовых маркеров, таких как выделение цветом, сопоставление фигурных скобок и маркеры ошибок. Вызовите метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> для завершения операторов и метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> для советов по методу. Для поддержки текстовых маркеров Отслеживайте эту команду, чтобы определить, требуется ли обновление маркеров в типизированном символе.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Посылается, когда пользователь вводит клавишу ВВОД. Отслеживайте эту команду, чтобы определить, когда следует отклонять окно подсказки метода, вызвав метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>. По умолчанию эта команда обрабатывается в текстовом представлении.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Посылается, когда пользователь вводит ключ Backspace. Монитор определяет, когда следует отклонять окно подсказки метода путем вызова метода <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>. По умолчанию эта команда обрабатывается в текстовом представлении.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Посылается из меню или с помощью сочетания клавиш. Вызовите метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>, чтобы обновить окно подсказки с помощью сведений о параметре.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Посылается, когда пользователь наводит указатель мыши на переменную или устанавливает курсор на переменную и выбирает **краткие сведения** из **IntelliSense** в меню **Правка** . Возвращайте тип переменной в подсказке, вызвав метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>. Если отладка активна, подсказка также должна показывать значение переменной.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Обычно отправляется, когда пользователь вводит CTRL + ПРОБЕЛ. Эта команда сообщает языковой службе о необходимости вызова метода <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> на <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Отправляется из меню, как правило, **Выбор комментариев** или **раскомментировать выделенный фрагмент** из **расширенного** меню **Правка** . <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> указывает, что пользователь хочет закомментировать выделенный текст.  <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> указывает, что пользователь хочет раскомментировать выделенный текст. Эти команды могут быть реализованы только языковой службой.|

## <a name="see-also"></a>См. также
- [Разработка языковой службы прежних версий](../../extensibility/internals/developing-a-legacy-language-service.md)
---
title: Важные команды для фильтров языковых служб (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb29ee5b5a5359d6cfe34911656dfe9be015262e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707615"
---
# <a name="important-commands-for-language-service-filters"></a>Важные команды для фильтров языковой службы
Если вы хотите создать полнофункциональный фильтр языкового сервиса, подумайте об обработке следующих команд. Полный список идентификаторов команд определяется в <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> перечислении управляемого кода и файле заголовка Stdidcmd.h для неуправляемого [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] кода. Вы можете найти файл Stdidcmd.h в *Visual Studio SDK путь установки*»VisualStudioIntegration »Общие.Ru.

## <a name="commands-to-handle"></a>Команды для обработки

> [!NOTE]
> Фильтрация для каждой команды в следующей таблице не является обязательной.

|Команда|Описание|
|-------------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Отправлено при нажатии на кнопку пользователя. Эта команда указывает, что пришло время предоставить меню ярлыка. Если вы не обрабатываете эту команду, текстовый редактор предоставляет меню ярлыка по умолчанию без каких-либо команд, конретизмовых для конкретного языка. Чтобы включить свои собственные команды в это меню, руните команду и отобразите меню ярлыка самостоятельно.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Обычно отправляется при вводе пользователем CTRL-J. Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> на, чтобы показать окно завершения оператора.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Отправка, когда пользователь вводит символ. Мониторинг этой команды, чтобы определить, когда символ триггера набран и обеспечить завершение оператора, советы метода и текстовые маркеры, такие как окраска синтаксиса, соответствие скобки и маркеры ошибок. Вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> метода <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> для завершения оператора <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> метода на советы метода. Чтобы поддерживать текстовые маркеры, отслеживайте эту команду, чтобы определить, требуется ли набранный символ обновить маркеры.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Отправка при вводе пользователя ключом Enter. Мониторинг этой команды, чтобы определить, когда отклонить <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> окно <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>наконечника метода, позвонив в метод на . По умолчанию текстовое представление обрабатывает эту команду.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Отправка при врачне пользователя клавиши Backspace. Монитор, чтобы определить, когда уволить окно <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> наконечник <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>метода, позвонив метод на . По умолчанию текстовое представление обрабатывает эту команду.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Отправлено из меню или клавиши ярлыка. Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> на обновление окна наконечника с информацией о параметре.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Отправлено, когда пользователь парит над переменной или позиционирует курсор на переменной и выбирает **Быструю информацию** из **IntelliSense** в меню **Edit.** Верните тип переменной в наконечнике, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> позвонив по методу <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>на . Если отладка активна, наконечник должен также отображать значение переменной.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Обычно отправляется при вводе пользователем CTRL-SPACEBAR. Эта команда говорит языковой <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> службе <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>вызвать метод на .|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Отправлено из меню, как правило, **Комментарий Выбор** или **Uncomment Выбор** из **Расширенный** в меню **edit.** <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>указывает на то, что пользователь хочет прокомментировать выбранный текст; <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> указывает на то, что пользователь хочет не прокомментировать выбранный текст. Эти команды могут быть реализованы только языковой службой.|

## <a name="see-also"></a>См. также
- [Разработка языковой службы прежних версий](../../extensibility/internals/developing-a-legacy-language-service.md)

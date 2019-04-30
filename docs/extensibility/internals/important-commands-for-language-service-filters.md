---
title: Важные команды для языковой службы фильтры | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ade4bdfce2cd01864075e02648f233622cafc61
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "63418426"
---
# <a name="important-commands-for-language-service-filters"></a>Важные команды для фильтров языковой службы
Если вы хотите создать фильтр службы полнофункциональный язык, рассмотрите возможность обработки команды. Полный список идентификаторов команд определяется в <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> перечисления для управляемого кода и заголовка Stdidcmd.h-файле для неуправляемого [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] кода. Чтобы найти файл Stdidcmd.h в *путь установки Visual Studio SDK*\VisualStudioIntegration\Common\Inc.

## <a name="commands-to-handle"></a>Команды для дескриптора

> [!NOTE]
> Это не обязательно для фильтрации для каждой команды в следующей таблице.

|Команда|Описание|
|-------------|-----------------|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Посылается, когда пользователь щелкает правой кнопкой мыши. Эта команда указывает, что это время создать контекстное меню. Если эта команда не обрабатывают, текстовый редактор предоставляет контекстное меню по умолчанию без любых команд для конкретного языка. Чтобы включить собственные команды этого меню, необходимо обработать команду и самостоятельного отображения контекстного меню.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Обычно отправляются, когда пользователь вводит CTRL + J. Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> для отображения поля завершения инструкции.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Посылается, когда пользователь вводит символ. Отслеживайте эту команду, чтобы определить, когда триггер символа и для предоставления инструкция завершения, метод советы и текстовых маркеров, таких как Цветовая разметка синтаксиса, парные фигурные скобки и маркеры ошибок. Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> для завершения операторов и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> для подсказок метода. Чтобы обеспечить поддержку меток текста, отслеживайте эту команду, чтобы определить, требуется ли обновить ваш маркеры, вводимый символ.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Посылается, когда пользователь вводит клавишу ВВОД. Отслеживать эту команду, чтобы определить, когда нужно закрыть окно подсказки метода путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>. По умолчанию представление текста обрабатывает эту команду.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Посылается, когда пользователь вводит клавишу Backspace. Монитор, чтобы определить, когда нужно закрыть окно подсказки метода путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>. По умолчанию представление текста обрабатывает эту команду.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Отправлено из меню или сочетания клавиш. Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> для обновления окна подсказки данных параметра.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Посылается, когда пользователь наводит переменной или помещает курсор на переменную и выбирает **краткие сведения** из **IntelliSense** в **изменить** меню. Тип возвращаемого значения переменной в подсказке по путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>. Если отладка будет активна, совет также должно отображаться значение переменной.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Обычно отправляются, когда пользователь вводит CTRL + ПРОБЕЛ. Эта команда определяет языковой службы для вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Отправленное через меню, обычно **выделенный фрагмент в комментарий** или **Раскомментировать выделенный фрагмент** из **Дополнительно** в **изменить** меню. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Указывает, что пользователь хочет закомментировать выделенный текст; <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> указывает, что пользователь хочет Раскомментировать выделенный текст. Эти команды можно реализовать только языковой службой.|

## <a name="see-also"></a>См. также
- [Разработка языковой службы прежних версий](../../extensibility/internals/developing-a-legacy-language-service.md)
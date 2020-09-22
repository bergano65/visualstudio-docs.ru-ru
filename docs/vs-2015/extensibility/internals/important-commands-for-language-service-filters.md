---
title: Важные команды для фильтров языковой службы | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 03bb20abf32f7c320ed56f4a649a9f43453e7694
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843032"
---
# <a name="important-commands-for-language-service-filters"></a>Важные команды для фильтров языковой службы
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Если вы хотите создать полнофункциональный фильтр языковой службы, рассмотрите возможность обработки следующих команд. Полный список идентификаторов команд определяется в <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> перечислении для управляемого кода и файла заголовка стдидкмд. h для неуправляемого [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] кода. Файл Стдидкмд. h можно найти в *пути установки Visual Studio SDK*\висуалстудиоинтегратион\коммон\инк.  
  
## <a name="commands-to-handle"></a>Команды для обработки  
  
> [!NOTE]
> Фильтрация для каждой команды в следующей таблице необязательна.  
  
|Команда|Description|  
|-------------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Посылается, когда пользователь щелкает правой кнопкой мыши. Эта команда указывает, что пора указать контекстное меню. Если эта команда не обрабатывается, текстовый редактор предоставляет контекстное меню по умолчанию без каких-либо команд, зависящих от языка. Чтобы включить в это меню собственные команды, обработайте команду и откройте контекстное меню самостоятельно.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Обычно отправляется, когда пользователь вводит CTRL + J. Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> метод для, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> чтобы отобразить поле завершения инструкции.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Посылается, когда пользователь вводит символ. Отслеживайте эту команду, чтобы определить, когда был введен символ триггера и что необходимо для завершения операторов, советов по методам и текстовых маркеров, таких как выделение цветом, сопоставление фигурных скобок и маркеры ошибок. Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> для завершения операторов for и метод для <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> советов по методу. Для поддержки текстовых маркеров Отслеживайте эту команду, чтобы определить, требуется ли обновление маркеров в типизированном символе.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Посылается, когда пользователь вводит клавишу ВВОД. Отслеживайте эту команду, чтобы определить, когда следует отклонять окно подсказки метода, вызвав <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> метод для <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> . По умолчанию эта команда обрабатывается в текстовом представлении.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Посылается, когда пользователь вводит ключ Backspace. Монитор позволяет определить, когда следует отклонять окно подсказки метода, вызвав <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> метод для <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> . По умолчанию эта команда обрабатывается в текстовом представлении.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Посылается из меню или с помощью сочетания клавиш. Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> метод в, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> чтобы обновить окно подсказки с помощью сведений о параметре.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Посылается, когда пользователь наводит указатель мыши на переменную или устанавливает курсор на переменную и выбирает **краткие сведения** из **IntelliSense** в меню **Правка** . Возвращайте тип переменной в подсказке, вызвав <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> метод в <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> . Если отладка активна, подсказка также должна показывать значение переменной.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Обычно отправляется, когда пользователь вводит CTRL + ПРОБЕЛ. Эта команда сообщает языковой службе о необходимости вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> метода для <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Отправляется из меню, как правило, **Выбор комментариев** или **раскомментировать выделенный фрагмент** из **расширенного** меню **Правка** . <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Указывает, что пользователь хочет закомментировать выделенный текст. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> указывает, что пользователь хочет раскомментировать выделенный текст. Эти команды могут быть реализованы только языковой службой.|  
  
## <a name="see-also"></a>См. также:  
 [Разработка языковой службы прежних версий](../../extensibility/internals/developing-a-legacy-language-service.md)

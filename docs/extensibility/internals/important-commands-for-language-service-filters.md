---
title: "Важные команд для языка службы фильтры | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: f6b5bad11c47074c29f3b319678419f1e42ab91b
ms.lasthandoff: 02/22/2017

---
# <a name="important-commands-for-language-service-filters"></a>Важные команды для фильтров службы языка
Если вы хотите создать фильтр службы полнофункциональный язык, рассмотрите возможность обработки команд. Полный список идентификаторов команд определяется в <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>перечисления для управляемого кода и заголовок Stdidcmd.h-файле для неуправляемого [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] кода.</xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Чтобы найти файл Stdidcmd.h в *путь установки Visual Studio SDK*\VisualStudioIntegration\Common\Inc.  
  
## <a name="commands-to-handle"></a>Команды для дескриптора  
  
> [!NOTE]
>  Не обязательна для фильтрации для каждой команды в следующей таблице.  
  
|Команда|Описание|  
|-------------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Посылается, когда пользователь щелкает правой кнопкой мыши. Эта команда указывает, что пора создать контекстное меню. Если эта команда не обрабатывают, текстовый редактор предоставляет контекстное меню по умолчанию без все команды конкретного языка. Чтобы включить собственные команды этого меню, обработку команды и отображения контекстного меню самостоятельно.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Как правило, передается при вводе CTRL + J. Вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>для отображения поля завершения инструкции.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Посылается, когда пользователь вводит символа. Отслеживайте эту команду, чтобы определить, когда триггер символа и выполнять инструкции завершения, метод советы и текстовых меток, таких как Цветовая подсветка синтаксиса, парные фигурные скобки и ошибка маркеры. Вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>для завершения операторов и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A>метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow>метод советы.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> Для поддержки текстовых меток, отслеживайте эту команду, чтобы определить, требуется ли обновить ваш маркеры, вводимый символ.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Посылается, когда пользователь вводит клавишу ВВОД. Отслеживать эту команду, чтобы определить, когда нужно закрыть окно подсказки метода путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>метода <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> По умолчанию текстовое представление обрабатывает эту команду.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Посылается, когда пользователь вводит клавишу Backspace. Монитор, чтобы определить, когда нужно закрыть окно подсказки метода путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A>метода <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> По умолчанию текстовое представление обрабатывает эту команду.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Отправлено из меню или сочетания клавиш. Вызов <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>для обновления сведений о параметре окно подсказки.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Посылается, когда пользователь наводит указатель мыши на переменную или помещает курсор на переменную и выбирает **краткие сведения** из **IntelliSense** в **изменить** меню. Возвращает тип переменной в подсказке, вызвав <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A>метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> Если отладка включена, совет также должны показывать значение переменной.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Как правило, передается при вводе CTRL + ПРОБЕЛ. Эта команда определяет языковую службу для вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>метода <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A>|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Обычно отправляются из меню, **выделенного фрагмента в комментарий** или **раскомментируйте выбора** из **Дополнительно** в **изменить** меню. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>Указывает, что пользователь хочет закомментируйте выделенного текста; <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>Указывает, что пользователь хочет раскомментируйте выделенный текст.</xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID></xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Эти команды может быть реализован только языковой службы.|  
  
## <a name="see-also"></a>См. также  
 [Разработка языковую службу для прежних версий](../../extensibility/internals/developing-a-legacy-language-service.md)

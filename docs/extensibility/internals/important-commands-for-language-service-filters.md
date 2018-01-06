---
title: "Важные команды для языка службы фильтры | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services, filters
- language services, commands to support
ms.assetid: 4948c494-3d4d-4f50-b3f9-959e73f90e4d
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: ee6c746874e7e00643f1b840185969a6dabadfe5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="important-commands-for-language-service-filters"></a>Важные команды для фильтров языковой службы
Если вы хотите создать фильтр службы полнофункциональный язык, рассмотрите возможность обработки команды. Полный список идентификаторов команд определяется в <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> перечисления для управляемого кода и заголовка Stdidcmd.h-файле для неуправляемого [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] кода. Чтобы найти файл Stdidcmd.h в *путь установки Visual Studio SDK*\VisualStudioIntegration\Common\Inc.  
  
## <a name="commands-to-handle"></a>Команды для обработки  
  
> [!NOTE]
>  Он не является обязательным для фильтрации для каждой команды в следующей таблице.  
  
|Команда|Описание:|  
|-------------|-----------------|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Посылается, когда пользователь щелкает правой кнопкой мыши. Эта команда указывает, что время для предоставления контекстное меню. Если эта команда не обрабатывают, текстовый редактор предоставляет контекстное меню по умолчанию без любые команды языка. Чтобы включить собственные команды меню, обработать команду и отображения контекстного меню самостоятельно.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Обычно отправляется, когда пользователь вводит CTRL + J. Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> Показывать окно завершения инструкции.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Посылается, когда пользователь вводит символ. Наблюдение за эту команду, чтобы определить, когда триггер символа и для предоставления инструкция завершения, метод советы и текстовых маркеров, как Цветовая разметка синтаксиса, парные фигурные скобки и ошибка маркеры. Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> для завершения операторов и <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow> метод советы. Для поддержки текстовых маркеров, наблюдение за эту команду, чтобы определить, требуется ли обновить ваш маркеры, вводимый символ.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Посылается, когда пользователь вводит клавишу ВВОД. Отслеживать эту команду, чтобы определить, когда нужно закрыть окно подсказки метод путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>. По умолчанию представления текста обрабатывает эту команду.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Посылается, когда пользователь вводит клавиша Backspace. Монитор, чтобы определить, когда нужно закрыть окно подсказки метод путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData.OnDismiss%2A> метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>. По умолчанию представления текста обрабатывает эту команду.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Отправлено из меню или сочетания клавиш. Вызовите <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> для обновления окна подсказки данных параметра.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Посылается, когда пользователь наведет переменной или помещает курсор на переменную и выбирает **краткие сведения** из **IntelliSense** в **изменить** меню. Тип возвращаемого значения переменной в подсказке путем вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateTipWindow%2A> метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>. Если отладка включена, совет также должны показывать значение переменной.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Обычно отправляется, когда пользователь вводит CTRL + ПРОБЕЛ. Эта команда определяет языковой службы для вызова <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>.|  
|<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID><br /><br /> <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>|Обычно отправляются в меню **выделенного фрагмента в комментарий** или **раскомментируйте выбора** из **Дополнительно** в **изменить** меню. <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>Указывает, что пользователь хочет закомментировать выделенный текст; <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> указывает, что пользователь хочет Раскомментировать выделенный текст. Эти команды может быть реализован только языковой службы.|  
  
## <a name="see-also"></a>См. также  
 [Разработка языковой службы прежних версий](../../extensibility/internals/developing-a-legacy-language-service.md)
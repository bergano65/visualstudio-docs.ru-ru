---
title: "\"Параметры\", \"Текстовый редактор\", \"C#\", \"Форматирование\" | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.NewLines
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Indentation
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.Wrapping
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting
- VS.ToolsOptionsPages.Text_Editor.CSharp.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting.Spacing
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Formatting
helpviewer_keywords:
- formatting [C#]
- formatting [J#]
- Text Editor Options dialog box, formatting
ms.assetid: 5a7bb668-1d0c-4ffe-9508-24592813162e
caps.latest.revision: 23
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: a157bb6b5e29bb90fcd033f58657887f610b4835
ms.contentlocale: ru-ru
ms.lasthandoff: 07/14/2017

---
# <a name="options-text-editor-c-formatting"></a>"Параметры", "Текстовый редактор", C#, "Форматирование"
Используйте диалоговое окно страницы свойств **Форматирование** для задания параметров форматирования кода в редакторе кода. Для доступа к этому диалоговому окну щелкните пункт **Параметры** в меню **Сервис**, разверните папки **Текстовый редактор** и **C#**, а затем выберите **Форматирование**.  
  
> [!NOTE]
>  Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в разделе [Персонализация интегрированной среды разработки Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="general-settings"></a>Общие параметры  
 Общие параметры определяют порядок применения редактором кода параметров форматирования к коду.  
  
## <a name="uielement-list"></a>Список элементов пользовательского интерфейса  
  
|Метка|Описание|  
|-----------|-----------------|  
|**Автоматически форматировать инструкции после ввода ;**|Если установлен этот флажок, форматирование инструкций выполняется по завершении в соответствии с выбранными для редактора кода параметрами. Снимите этот флажок, если вы не хотите, чтобы редактор кода изменял инструкции.|  
|**Автоматически форматировать закрытые блоки после ввода }**|Если установлен этот флажок, форматирование блоков кода выполняется в соответствии с выбранными для редактора кода параметрами, как только завершается блок кода. Снимите этот флажок, если вы не хотите, чтобы редактор кода изменял блоки.|  
|**Определять отступ при вставке**|Если установлен этот флажок, форматирование текста, вставляемого в редакторе кода, выполняется в соответствии с выбранными для редактора кода параметрами. Снимите этот флажок, если вы не хотите, чтобы вставляемый текст изменялся.|  
  
## <a name="preview-window"></a>Окно предварительного просмотра  
 Области параметров **Отступ**, **Новые строки**, **Интервалы** и **Перенос по словам** отображают окно предварительного просмотра. В окне предварительного просмотра виден результат применения этих параметров. Чтобы использовать окно предварительного просмотра, выберите параметр форматирования. В окне предварительного просмотра отображается пример выбранного параметра. При изменении настройки, например при установке или снятии флажка, содержимое окна предварительного просмотра меняется, отображая эффект применения новой настройки.  
  
## <a name="remarks"></a>Примечания  
 Параметры отступов на страницах **Табуляция** для каждого языка определяют только место, в которое редактор кода помещает курсор при нажатии клавиши ВВОД в конце строки. Параметры отступов в разделе **Форматирование** применяются при автоматическом форматировании кода, например при вставке кода в файл с установленным флажком **Определять отступ при вставке**, а также когда форматируемый блок вводится вручную.  
  
## <a name="see-also"></a>См. также  
 [Страница "Общие", папка "Среда", диалоговое окно "Параметры"](../../ide/reference/general-environment-options-dialog-box.md)

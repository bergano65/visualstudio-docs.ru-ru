---
title: "Поддержка панели навигации в языковую службу прежних версий | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Navigation bar, supporting in language services [managed package framework]
- language services [managed package framework], Navigation bar
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: eb5212c4828ad24256447bc1c75f85ec0d9d9579
ms.contentlocale: ru-ru
ms.lasthandoff: 09/06/2017

---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>Поддержка панели навигации в языковую службу прежних версий
На панели навигации в верхней части редактора представления отображаются типы и члены в файле. В левом раскрывающемся списке отображаются типы и элементы отображаются в правом раскрывающегося списка. Когда пользователь выбирает тип, курсор помещается в первой строке типа. Когда пользователь выбирает элемент, курсор помещается в определении элемента. Раскрывающиеся списки будут обновлены в соответствии с текущей позиции курсора.  
  
## <a name="displaying-and-updating-the-navigation-bar"></a>Отображения и обновления на панели навигации  
 Для поддержки панели навигации, должен быть производным от класса <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> класса и реализовать <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> метод. При языковой службы предоставляется окно кода базовый <xref:Microsoft.VisualStudio.Package.LanguageService> класс создает экземпляры <xref:Microsoft.VisualStudio.Package.CodeWindowManager>, который содержит <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> объект, представляющий окно кода. <xref:Microsoft.VisualStudio.Package.CodeWindowManager> Объект предоставляется новый <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> объекта. <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> Возвращает метод <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> объекта. Если возвращается экземпляр вашего <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> класса, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> вызовы вашего <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> метод для заполнения внутренний список и передает вашей <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> объект [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] раскрывающийся список панели диспетчера. В раскрывающемся списке панели диспетчера, в свою очередь, вызывает <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A> метод для вашего <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> для установления <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> объект, содержащий два раскрывающиеся строки.  
  
 Когда курсор перемещается, <xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> вызовы метода <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> метод. Базовый <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> вызовы метода <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> метод в вашей <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> класса для обновления состояния на панели навигации. Передайте набор <xref:Microsoft.VisualStudio.Package.DropDownMember> объекты в этот метод. Каждый объект представляет запись, в раскрывающемся списке.  
  
## <a name="the-contents-of-the-navigation-bar"></a>Содержимое панели навигации  
 На панели навигации обычно содержит список типов и список элементов. Список типов включает все типы, доступные в текущем файле исходного кода. Имена типов, которые включают сведения полное пространство имен. Ниже приведен пример кода C# с двумя типами:  
  
```csharp  
namespace TestLanguagePackage  
{  
    public class TestLanguageService  
    {  
        internal struct Token  
        {  
            int tokenID;  
        }  
        private Tokens[] tokens;  
        private string serviceName;  
    }  
}  
```  
  
 Отображает список типов `TestLanguagePackage.TestLanguageService` и `TestLanguagePackage.TestLanguageService.Tokens`.  
  
 Список членов отображает доступные элементы типа, выбранного в списке типов. Использование в коде выше, если `TestLanguagePackage.TestLanguageService` — тип, который выбран, список элементов будет содержать закрытые члены `tokens` и `serviceName`. Внутренняя структура `Token` не отображается.  
  
 Вы можете реализовать список элементов, чтобы сделать имя члена полужирным, когда курсор помещается внутри него. Члены могут также отображаться в серым цветом текста, указывающее на то, что они не находятся в области, в которой расположен курсор.  
  
## <a name="enabling-support-for-the-navigation-bar"></a>Включение поддержки для панели навигации  
 Чтобы включить поддержку на панели навигации, необходимо задать `ShowDropdownBarOption` параметр <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> атрибут `true`. Этот параметр задает свойство <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>. Для поддержки панели навигации, необходимо реализовать <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> объекта в <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> метод <xref:Microsoft.VisualStudio.Package.LanguageService> класса.  
  
 В реализации <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> метод, если <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> свойству `true`, можно вернуть <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> объекта. Если вы не возвращают объект, на панели навигации не отображается.  
  
 Параметр для отображения на панели навигации можно задать пользователем, поэтому возможно, для этого элемента управления будут сброшены при открытом представление редактора. Пользователь должен закрыть и снова откройте окно редактора, чтобы изменения вступили в месте.  
  
## <a name="implementing-support-for-the-navigation-bar"></a>Реализация поддержки для панели навигации  
 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> Метод принимает два списка (по одному для каждого раскрывающегося списка) и два значения, представляющий текущее выделение в каждом списке. Списки и выбора значения могут быть обновлены, в этом случае <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> метод должен возвращать `true` для указания, что списки были изменены.  
  
 При изменении выделения в раскрывающийся список типов, необходимо обновить список членов в соответствии с новым типом. Элементы, отображаемые в списке элементов может быть как:  
  
-   Список элементов для текущего типа.  
  
-   Всех членов, доступных в источнике файл, но со всеми элементами не в текущем типе, отображаются серым текстом. Пользователь по-прежнему можно выбрать элементы показаны серым цветом, поэтому их можно использовать для быстрого перемещения, но цвет указывает, что они не являются частью текущего выбранного типа.  
  
 Реализация <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> метода, как правило, выполняет следующие действия:  
  
1.  Получите список объявлений текущего файла исходного кода.  
  
     Существует несколько способов заполнения списков. Один подход заключается в создании пользовательского метода в версии <xref:Microsoft.VisualStudio.Package.LanguageService> класс, который вызывает <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод синтаксического анализа пользовательские причину, которая возвращает список всех объявлений. Другой подход может быть вызов <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод непосредственно из <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> метода с указанием причины пользовательских синтаксического анализа. Третий способ может быть кэширование объявления в <xref:Microsoft.VisualStudio.Package.AuthoringScope> класса, возвращаемыми последней операции полного синтаксического анализа в <xref:Microsoft.VisualStudio.Package.LanguageService> класса и извлечения, из <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> метод.  
  
2.  Заполнение или обновить список типов.  
  
     Содержимое списка типов могут обновляться при изменении источника или если вы решили изменить стиль текста типов, в зависимости от текущей позиции курсора. Обратите внимание, что эта позиция передается <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> метод.  
  
3.  Определение типа для выбора в списке типов, в зависимости от текущей позиции курсора.  
  
     Поиск объявлений, которые были получены на шаге 1, чтобы определить его тип, включающий текущей позиции курсора и найдите в списке типов для данного типа определить его индекс в списке типов.  
  
4.  Заполнение или обновить список членов, в зависимости от выбранного типа.  
  
     Отражает список элементов, отображаемых в **члены** раскрывающегося списка. Содержимое списка членов может потребоваться обновить при изменении источника или если отображаются только элементы выбранного типа и изменении выбранного типа. Если выбрано для отображения всех элементов в исходном файле, стиль текста каждого элемента в списке должен быть обновлен при изменении выбранного типа.  
  
5.  Определите элемент, чтобы выбрать в списке элементов, в зависимости от текущей позиции курсора.  
  
     Поиск члена, который содержит текущее положение курсора в объявлениях, которые были получены на шаге 1, а затем выполнить поиск в списке членов для этого элемента определить его индекс в списке членов.  
  
6.  Возвращает `true` Если внесены изменения в списки или выбранные элементы в любом из списков.

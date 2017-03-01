---
title: "Поддержка панели навигации в языковую службу для прежних версий | Документы Microsoft"
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 88636468da333fd9200f8661d88af6e7fdeedc59
ms.lasthandoff: 02/22/2017

---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>Поддержка панели навигации в языковую службу для прежних версий
На панели навигации в верхней части редактора представления отображаются типы и члены в файле. В левом раскрывающемся списке отображаются типы и члены отображаются в правом раскрывающемся списке. Когда пользователь выбирает тип, курсор помещается в первой строке типа. Когда пользователь выбирает элемент, курсор помещается в определении элемента. Раскрывающиеся списки будут обновлены в соответствии с текущей позиции курсора.  
  
## <a name="displaying-and-updating-the-navigation-bar"></a>Отображения и обновления на панели навигации  
 Для поддержки панели навигации, необходимо создать производный класс от <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>класса и реализовать <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>метод.</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> Если службе языка присвоено окно кода базовый <xref:Microsoft.VisualStudio.Package.LanguageService>создает экземпляр класса <xref:Microsoft.VisualStudio.Package.CodeWindowManager>, который содержит <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow>объект, представляющий окно кода.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> </xref:Microsoft.VisualStudio.Package.CodeWindowManager> </xref:Microsoft.VisualStudio.Package.LanguageService> <xref:Microsoft.VisualStudio.Package.CodeWindowManager>Объект предоставляется новый <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>объекта.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> </xref:Microsoft.VisualStudio.Package.CodeWindowManager> <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>Возвращает метод <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>объекта.</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> </xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> Если вернуть экземпляр вашего <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>класс, <xref:Microsoft.VisualStudio.Package.CodeWindowManager>вызовы вашего <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>способ заполнения внутренний список и передает вашей <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>объект [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] раскрывающийся список панели диспетчера.</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> </xref:Microsoft.VisualStudio.Package.CodeWindowManager> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> В раскрывающемся списке панели manager, в свою очередь, вызывает <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A>метод вашей <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>для установления <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar>объект, содержащий два раскрывающиеся строки.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A>  
  
 При перемещении курсора, <xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A>вызовы метода <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A>метод.</xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> </xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> Базовый <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A>метод вызывает <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>метод в своем <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>классе для обновления состояния на панели навигации.</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> </xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> Пройти набор <xref:Microsoft.VisualStudio.Package.DropDownMember>объекты в этот метод.</xref:Microsoft.VisualStudio.Package.DropDownMember> Каждый объект представляет запись в раскрывающемся списке.  
  
## <a name="the-contents-of-the-navigation-bar"></a>Содержимое панели навигации  
 На панели навигации обычно содержит список типов и список членов. Список типов включает все типы, доступные в текущем исходном файле. Имена типов, которые включают сведения полное пространство имен. Ниже приведен пример кода C# с двумя типами:  
  
```c#  
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
  
 Список членов отображает доступные элементы типа, выбранного в списке типов. Использование в примере выше, если `TestLanguagePackage.TestLanguageService` — тип, который выбран, список будет содержать закрытые члены `tokens` и `serviceName`. Внутренняя структура `Token` не отображается.  
  
 Можно реализовать список элементов, чтобы сделать имя члена полужирным, когда курсор помещается внутри него. Члены могут также отображаться в серым цветом текста, указывающее на то, что они не находятся в области, в которой расположен курсор.  
  
## <a name="enabling-support-for-the-navigation-bar"></a>Поддержка панели навигации  
 Чтобы включить поддержку на панели навигации, необходимо установить `ShowDropdownBarOption` параметр <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>атрибут `true`.</xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Этот параметр задает <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>Свойства.</xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> Для поддержки панели навигации, необходимо реализовать <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>объект в <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>метод <xref:Microsoft.VisualStudio.Package.LanguageService>класса.</xref:Microsoft.VisualStudio.Package.LanguageService> </xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> </xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>  
  
 В своей реализации <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>метод, если <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>свойству `true`, можно вернуть <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>объекта.</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> </xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> </xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> Если вы не возвращают объект, на панели навигации не отображается.  
  
 Можно задать параметр для отображения на панели навигации пользователем, поэтому возможно для этого элемента управления для сброса, когда открыто представление редактора. Пользователь должен закрыть и снова открыть окно редактора, прежде чем изменения вступят в силу.  
  
## <a name="implementing-support-for-the-navigation-bar"></a>Реализация поддержки панели навигации  
 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>Метод принимает два списка (по одному для каждого раскрывающегося списка) и два значения, представляющий текущее выделение в каждом списке.</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> Списки и выбора значения могут быть обновлены, в этом случае <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>метод должен возвращать `true` для указания, что списки изменились.</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>  
  
 При изменении выделения в раскрывающемся списке типов, необходимо обновить список членов в соответствии с новым типом. Как показано в списке элементов может быть:  
  
-   Список элементов для текущего типа.  
  
-   Всех членов, доступных в источнике файл, но со всеми членами группы не в текущем типе отображаются серым текстом. Пользователь может выбрать членов серым, по-прежнему может использоваться для быстрых переходов, но цвет указывает, что они не являются частью выбранного типа.  
  
 Реализация <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>обычно выполняет следующие шаги:</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>  
  
1.  Получите список текущего объявления для исходного файла.  
  
     Существует ряд способов для заполнения списков. Один подход заключается в создании пользовательского метода в версии <xref:Microsoft.VisualStudio.Package.LanguageService>класс, который вызывает <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>Причина пользовательского синтаксического анализа, который возвращает список всех объявлений метода.</xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> </xref:Microsoft.VisualStudio.Package.LanguageService> Другой подход может быть вызов <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>напрямую из <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>метод синтаксического анализа пользовательские причина.</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> </xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Третий подход может быть кэширование объявления в <xref:Microsoft.VisualStudio.Package.AuthoringScope>класса, возвращаемыми последней операции полного анализа в <xref:Microsoft.VisualStudio.Package.LanguageService>класса и извлечения, из <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>метод.</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> </xref:Microsoft.VisualStudio.Package.LanguageService> </xref:Microsoft.VisualStudio.Package.AuthoringScope>  
  
2.  Заполнение или обновить список типов.  
  
     Содержимое списка типов могут обновляться при изменении источника или если вы решили изменить стиль текста типов, в зависимости от текущей позиции курсора. Обратите внимание, что эта позиция передается <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>метод.</xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A>  
  
3.  Определение типа для выбора в списке типов, в зависимости от текущей позиции курсора.  
  
     Поиск объявлений, которые были получены на шаге 1 для поиска типа, ограничивающий текущей позиции курсора и найдите в списке типов для данного типа определить его индекс в списке типов.  
  
4.  Заполнение или обновить список членов на основе выбранного типа.  
  
     Отражает список элементов, отображаемых в **элементы** раскрывающегося списка. Содержимое элементов списка может потребоваться обновить, если источник изменился или отображаются только элементы выбранного типа и изменении выбранного типа. Если выбрано для отображения всех элементов в исходном файле, стиль текста для каждого элемента в списке должен обновляться при изменении выбранного типа.  
  
5.  Определите элемент, чтобы выбрать в списке элементов, в зависимости от текущей позиции курсора.  
  
     Поиск члена, который содержит текущее положение курсора в объявления, которые были получены на шаге 1, а затем найдите список элементов для этого элемента определить его индекс в списке членов.  
  
6.  Возвращает `true` Если были внесены изменения списков или выбранные элементы в списке.

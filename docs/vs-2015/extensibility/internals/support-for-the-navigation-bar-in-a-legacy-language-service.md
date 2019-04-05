---
title: Поддержка панели навигации в языковой службе прежних версий | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Navigation bar, supporting in language services [managed package framework]
- language services [managed package framework], Navigation bar
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 714e4a24ae6dc2c345b97bbd6e080b0c987f65f7
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/23/2019
ms.locfileid: "58991346"
---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>Поддержка панели навигации в языковой службе прежних версий
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

На панели навигации в верхней части редактора представления отображает типы и члены в файле. В левом раскрывающемся списке отображаются типы и члены отображаются в правом раскрывающегося списка. Когда пользователь выбирает тип, курсор помещается в первой строке типа. Когда пользователь выбирает элемент, курсор помещается в определении элемента. Раскрывающиеся списки обновляются для отображения текущего положения курсора.  
  
## <a name="displaying-and-updating-the-navigation-bar"></a>Отображения и обновления на панели навигации  
 Для поддержки панели навигации, должен быть производным от класса <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> класса и реализуйте <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> метод. Когда службы вашего языка предоставляется окно кода, базовый <xref:Microsoft.VisualStudio.Package.LanguageService> создает экземпляр класса <xref:Microsoft.VisualStudio.Package.CodeWindowManager>, который содержит <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> объект, представляющий окно кода. <xref:Microsoft.VisualStudio.Package.CodeWindowManager> Объект предоставляется новый <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> объекта. <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> Метод получает <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> объекта. Если возвращается экземпляр вашего <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> класс, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> вызовы вашего <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> способ заполнения внутренний список и передает вашей <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> объект [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] раскрывающейся панели диспетчера. В раскрывающемся списке панели manager, в свою очередь, вызывает <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A> метод вашей <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> для установления <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> объект, содержащий два раскрывающиеся панели.  
  
 При перемещении курсора, <xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> вызовы методов <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> метод. Базовый <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> вызовы методов <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> метод в вашей <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> класса для обновления состояния на панели навигации. Передать набор <xref:Microsoft.VisualStudio.Package.DropDownMember> объекты в этот метод. Каждый объект представляет запись в раскрывающемся списке.  
  
## <a name="the-contents-of-the-navigation-bar"></a>Содержимое панели навигации  
 На панели навигации обычно содержит список типов и списком членов. Список типов представлены все типы, доступные в текущем исходном файле. Имена типов включают сведения о пространстве имен завершения. Ниже приведен пример кода C# с двумя типами:  
  
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
  
 Отобразится список типов `TestLanguagePackage.TestLanguageService` и `TestLanguagePackage.TestLanguageService.Tokens`.  
  
 В списке членов отображаются доступные члены типа, который выбран в списке типов. Использование в примере выше, если `TestLanguagePackage.TestLanguageService` — тип, который выбран, в список элементов будет содержать закрытые члены `tokens` и `serviceName`. Внутренняя структура `Token` не отображается.  
  
 Вы можете реализовать списка членов, чтобы сделать имя члена полужирным шрифтом, когда курсор помещается внутри него. Члены могут также отображаться в затененный текст, указывающее, что они не находятся в области, где в данный момент находится курсор.  
  
## <a name="enabling-support-for-the-navigation-bar"></a>Поддержка панели навигации  
 Чтобы включить поддержку для панели навигации, необходимо задать `ShowDropdownBarOption` параметр <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> атрибут `true`. Этот параметр задает свойство <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>. Для поддержки панели навигации, необходимо реализовать <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> объекта в <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> метод <xref:Microsoft.VisualStudio.Package.LanguageService> класса.  
  
 В реализации <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> метод, если <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> свойству `true`, можно вернуть <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> объекта. Если вы не возвращают объект, на панели навигации не отображается.  
  
 Для отображения на панели навигации можно включить на пользователем, так что вполне возможно, для этого элемента управления нужно сбросить при открытом представлении редактора. Пользователь должен закрыть и снова открыть окно редактора, прежде чем изменения вступят в силу.  
  
## <a name="implementing-support-for-the-navigation-bar"></a>Реализация поддержки для панели навигации  
 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> Метод принимает два списка (по одному для каждого раскрывающегося списка) и два значения, представляющий текущее выделение в каждом списке. Списки и выбора значения могут быть обновлены, в этом случае <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> метод должен возвращать `true` для указания, что списки были изменены.  
  
 При изменении выделения в раскрывающемся списке типов, необходимо обновить список членов в соответствии с новым типом. То, что отображается в списке элементов может быть либо:  
  
- Список элементов для текущего типа.  
  
- Все элементы, доступные в источнике файл, но со всеми членами не в текущем типе, отображаются серым шрифтом. Пользователь по-прежнему можно выбрать элементы закрашены серым, поэтому они могут использоваться для быстрой навигации, но цвет указывает, что они не являются частью текущего выбранного типа.  
  
  Реализация <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> метода обычно выполняет следующие действия:  
  
1.  Получение списка текущие объявления для исходного файла.  
  
     Существует ряд способов для заполнения списков. Один подход заключается в создании пользовательского метода в версии <xref:Microsoft.VisualStudio.Package.LanguageService> класса, который вызывает <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод с причиной пользовательского синтаксического анализа, который возвращает список всех объявлений. Другой подход может быть вызов <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> напрямую из <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> метода с указанием причины пользовательского синтаксического анализа. Третий подход может быть кэшировать объявления в <xref:Microsoft.VisualStudio.Package.AuthoringScope> возвращается с последней операции полного синтаксического анализа в <xref:Microsoft.VisualStudio.Package.LanguageService> класса и извлечения, из <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> метод.  
  
2.  Заполнить или обновить список типов.  
  
     Содержимое списка типов могут обновляться при изменении источника или если вы собираетесь изменить стиль текста из типов, в зависимости от текущей позиции курсора. Обратите внимание, что эта позиция передается <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> метод.  
  
3.  Определите тип для выбора в списке типов, в зависимости от текущей позиции курсора.  
  
     Можно искать объявления, которые были получены на шаге 1, чтобы найти тип, который содержит текущее положение курсора и найдите в списке типов для этого типа определить его индекс в списке типов.  
  
4.  Заполнить или обновить список членов, в зависимости от выбранного типа.  
  
     Отражает список элементов, отображаемых в **члены** раскрывающегося списка. Содержимое списка членов может потребоваться обновляться в случае изменения источника или если отображаются только элементы выбранного типа и выбранного типа изменилось. Если выбрано для отображения всех элементов в исходном файле, стиль текста каждого элемента в списке должен обновляться, если текущий выбранный тип был изменен.  
  
5.  Определите элемент для выбора в списке элементов, в зависимости от текущей позиции курсора.  
  
     Поиск объявлений, которые были получены на шаге 1 элемента, который содержит текущее положение курсора, а затем найдите в списке членов для этого элемента определить его индекс в списке членов.  
  
6.  Вернуть `true` Если внесены изменения в списки или выбранные элементы в любом из списков.

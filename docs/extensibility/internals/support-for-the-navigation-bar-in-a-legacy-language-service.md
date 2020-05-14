---
title: Поддержка панели навигации в службе языка Legacy (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Navigation bar, supporting in language services [managed package framework]
- language services [managed package framework], Navigation bar
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f86dabb0594b1e33c45808efb387fcbe313e3de3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704864"
---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>Поддержка панели навигации в языковой службе прежних версий
Панель навигации в верхней части представления редактора отображает типы и элементов в файле. Типы отображаются в левом падении вниз, а участники отображаются в правом падении. Когда пользователь выбирает тип, карет помещается на первую строку типа. Когда пользователь выбирает участника, карет помещается на определение участника. Выпадающие коробки обновляются, чтобы отразить текущее местоположение caret.

## <a name="displaying-and-updating-the-navigation-bar"></a>Отображение и обновление панели навигации
 Для поддержки панели навигации необходимо извлечь <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> класс из <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> класса и реализовать метод. Когда вашей языковой службе предоставляется кодовое окно, базовый <xref:Microsoft.VisualStudio.Package.LanguageService> класс мгновенно <xref:Microsoft.VisualStudio.Package.CodeWindowManager>вызывает, что <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> содержит объект, представляющий окно кода. Затем <xref:Microsoft.VisualStudio.Package.CodeWindowManager> объекту предоставляется <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> новый объект. Метод <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> получает <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> объект. Если вы возвращаете <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> экземпляр вашего класса, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> ваш <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> метод заселяет внутренние списки и передает объект <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> диспетчеру [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] барной стойки. Менеджер барной панели, в свою <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A> очередь, <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> вызывает метод <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> на объекте, чтобы установить объект, который держит два выпадающих бара.

 Когда карет движется, <xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> метод <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> вызывает метод. Базовый <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> метод <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> вызывает метод <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> в классе для обновления состояния панели навигации. Вы передают набор <xref:Microsoft.VisualStudio.Package.DropDownMember> объектов этому методу. Каждый объект представляет собой запись в выпадении вниз.

## <a name="the-contents-of-the-navigation-bar"></a>Содержимое панели навигации
 Панель навигации обычно содержит список типов и список участников. Список типов включает все типы, доступные в текущем файле исходного кода. Имена типов включают полную информацию о пространстве имен. Ниже приводится пример кода СИ с двумя типами:

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

 Список типов `TestLanguagePackage.TestLanguageService` будет `TestLanguagePackage.TestLanguageService.Tokens`отображаться и .

 Список участников отображает доступные участники типа, выбранного в списке типов. Используя приведенный выше `TestLanguagePackage.TestLanguageService` пример кода, если выбран тип, список участников будет содержать частных членов `tokens` и `serviceName`. Внутренняя `Token` структура не отображается.

 Вы можете реализовать список членов, чтобы сделать имя члена смелым, когда карета находится внутри него. Участники также могут отображаться в сером тексте, указывая, что они не находятся в пределах сферы, где в настоящее время находится карет.

## <a name="enabling-support-for-the-navigation-bar"></a>Включение поддержки панели навигации
 Для поддержки панели навигации необходимо `ShowDropdownBarOption` установить <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> параметр `true`атрибута. Этот параметр задает свойство <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A>. Для поддержки панели навигации <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> необходимо реализовать <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> объект <xref:Microsoft.VisualStudio.Package.LanguageService> в методе в классе.

 При реализации <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> метода, <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> если свойство `true`настроено на, вы можете вернуть <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> объект. Если вы не вернете объект, панель навигации не отображается.

 Возможность отображить панель навигации может быть установлена пользователем, поэтому этот элемент управления может быть сдан во время открытия представления редактора. Пользователь должен закрыть и вновь открыть окно редактора до изменения.

## <a name="implementing-support-for-the-navigation-bar"></a>Реализация поддержки панели навигации
 Метод <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> занимает два списка (по одному для каждого выпадения) и два значения, представляющие текущий выбор в каждом списке. Списки и значения выбора могут быть обновлены, и в этом случае <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> метод должен вернуться, `true` чтобы указать, что списки изменились.

 По мере изменения выбора в типах выпадающих типов список участников должен обновляться, чтобы отразить новый тип. То, что отображается в списке участников, может быть либо:

- Список участников для текущего типа.

- Все участники доступны в исходном файле, но со всеми участниками, не в текущем типе отображается в седой текст. Пользователь по-прежнему может выбрать серые из членов, так что они могут быть использованы для быстрой навигации, но цвет указывает, что они не являются частью выбранного в настоящее время типа.

  Реализация метода <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> обычно выполняет следующие действия:

1. Получите список текущих деклараций для исходного файла.

     Есть несколько способов заполнить списки. Один из подходов заключается в создании <xref:Microsoft.VisualStudio.Package.LanguageService> пользовательского <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метода в версии класса, который вызывает метод с пользовательской причиной разбора, которая возвращает список всех деклараций. Другой подход может заключаться в вызове метода <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> непосредственно из метода <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> с пользовательской причиной разбора. Третий подход может заключаться в кэшировании деклараций в <xref:Microsoft.VisualStudio.Package.AuthoringScope> классе, <xref:Microsoft.VisualStudio.Package.LanguageService> возвращенных последней <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> полной операцией разбора в классе, и извлечении их из метода.

2. Заполнить или обновить список типов.

     Содержимое списка типов может быть обновлено при изменении источника или при выборе текста в отношении типов на основе текущего положения caret. Обратите внимание, что эта <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> позиция передается методу.

3. Определите тип, выбранный в списке типов, на основе текущей позиции caret.

     Вы можете искать декларации, полученные в шаге 1, чтобы найти тип, который примыкает к текущей позиции caret, а затем искать список типов для этого типа, чтобы определить его индекс в список типов.

4. Заполнить или обновить список членов на основе выбранного типа.

     Список участников отражает то, что в настоящее время отображается в отсечении **участников.** Содержимое списка участников может потребоваться обновить, если источник изменился или если вы отображаете только члены выбранного типа и выбранный тип изменился. Если вы решите отобразить всех участников в исходном файле, то стиль текста каждого участника в списке должен быть обновлен, если выбранный в настоящее время тип изменился.

5. Определите участника для выбора в списке членов на основе текущей позиции caret.

     Поиск деклараций, полученных в шаге 1 для участника, который содержит текущее положение caret, а затем поиск списка членов для этого члена, чтобы определить его индекс в список участников.

6. Возврат, `true` если какие-либо изменения были внесены в списки или выбор в любом списке.

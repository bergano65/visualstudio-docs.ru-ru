---
title: Структурирование в языковой службе прежних версий | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7af8ab4615cff7462a47dfb11b193660eb62274c
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66314882"
---
# <a name="outlining-in-a-legacy-language-service"></a>Структурирование в языковой службе прежних версий
Структурирование позволяет свернуть сложную программу в обзор или структуры. Например в C# можно свернуть все методы в одну строку, содержащую только сигнатуру метода. Кроме того структуры и классы можно свернуть, чтобы отобразить только имена структур и классов. Из единственного метода сложную логику можно свернуть, чтобы показать Общая последовательность действий, отображая только первая часть инструкции, такие как `foreach`, `if`, и `while`.

 Устаревший языковой службы реализуются как часть пакета VSPackage, но новый способ реализовать функции языковой службы является использование расширений MEF. Дополнительные сведения см. в разделе [Пошаговое руководство: структуризация](../../extensibility/walkthrough-outlining.md).

> [!NOTE]
> Мы рекомендуем начать использовать новый редактор API как можно скорее. Это улучшит производительность службы языка и позволяют воспользоваться преимуществами новых функций редактора.

## <a name="enabling-support-for-outlining"></a>Включение поддержки для структуры
 `AutoOutlining` Запись реестра имеет значение 1, чтобы включить автоматическую структуризацию. Автоматическое структурирование устанавливает синтаксического анализа всего источника при загрузке или изменен для выявления скрытых областей и показывать структурирования глифы файла. Структурирование можно также управлять вручную пользователем.

 Значение `AutoOutlining` запись реестра можно получить с помощью <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> свойство <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класса. `AutoOutlining` Запись реестра можно инициализировать с помощью именованного параметра <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> атрибутов (см. в разделе [регистрация языковой службы прежних](../../extensibility/internals/registering-a-legacy-language-service1.md) сведения).

## <a name="the-hidden-region"></a>Скрытой области
 Чтобы предоставить структурирование, языковой службы должен поддерживать скрытых областей. Это те диапазоны текста, который можно разворачивать и сворачивать. Скрытые области могут разделяться символами стандартного языка, например фигурные скобки, или пользовательские символы. Например, C# имеет `#region` / `#endregion` пару, которая разделяет скрытой области.

 Скрытые области управляются диспетчером скрытой области, который указывается в виде <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> интерфейс.

 Структурирование использует скрытых областей <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> интерфейс и содержать диапазон скрытой области, текущее состояние отображения и баннер для отображения при сворачивании области.

 Использует средство синтаксического анализа языка службы <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> метод, чтобы добавить новую скрытую область с поведением по умолчанию для скрытых областей, хотя <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> метод позволяет настроить внешний вид и поведение структуры. После сеанса скрытой области, получают скрытые области [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] управляет скрытых областей для языковой службы.

 Если вам нужно определить, когда уничтожается сеанса скрытой области, скрытой области изменяется, или вам нужно убедиться, что определенной скрытой области является видимым. должен быть производным от класса <xref:Microsoft.VisualStudio.Package.Source> класса и переопределить соответствующие методы <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A>, <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A>, и <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>, соответственно.

### <a name="example"></a>Пример
 Ниже приведен упрощенный пример создания скрытых областей для всех пар фигурных скобок. Предполагается, что язык предоставляет парные фигурные скобки и фигурные скобки для сопоставления по крайней мере включая фигурные скобки ({и}). Этот подход является только для иллюстративных целей. Полная реализация будет иметь полный обработки случаев в <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>. В этом примере также показано, как задать <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> предпочтение `true` временно. Альтернативным вариантом является указание `AutoOutlining` именованный параметр в `ProvideLanguageServiceAttribute` атрибут в языковой пакет.

 В этом примере предполагается, что C# правила для комментариев, строк и литералы.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace MyLanguagePackage
{

    public class MyLanguageService : LanguageService
    {
        private LanguagePreferences m_preferences;

        public override LanguagePreferences  GetLanguagePreferences()
        {
            if (m_preferences == null)
            {
                m_preferences = new LanguagePreferences(this.Site,
                                                        typeof(MyLanguageService).GUID,
                                                        Name);
                m_preferences.Init();
                // Temporarily enabled auto-outlining
                m_preferences.AutoOutlining = true;
            }
            return m_preferences;
        }

        public override AuthoringScope  ParseSource(ParseRequest req)
        {
            Source source = (Source) this.GetSource(req.FileName);
            switch (req.Reason)
            {
               case ParseReason.HighlightBraces:
               case ParseReason.MatchBraces:
               case ParseReason.MemberSelectAndHighlightBraces:
                  if (source.Braces != null)
                  {
                      foreach (TextSpan[] brace in source.Braces)
                      {
                         if (brace.Length == 2)
                         {
                             if (req.Sink.HiddenRegions == true
                                   && source.GetText(brace[0]).Equals("{")
                                   && source.GetText(brace[1]).Equals("}"))
                             {
                                //construct a TextSpan of everything between the braces
                                TextSpan hideSpan = new TextSpan();
                                hideSpan.iStartIndex = brace[0].iStartIndex;
                                hideSpan.iStartLine = brace[0].iStartLine;
                                hideSpan.iEndIndex = brace[1].iEndIndex;
                                hideSpan.iEndLine = brace[1].iEndLine;
                                req.Sink.ProcessHiddenRegions = true;
                                req.Sink.AddHiddenRegion(hideSpan);
                             }
                             req.Sink.MatchPair(brace[0], brace[1], 1);
                         }
                         else if (brace.Length >= 3)
                             req.Sink.MatchTriple(brace[0], brace[1], brace[2], 1);
                  }
        }
                   break;
               default:
                   break;
      }
            // Must always return a valid AuthoringScope object.
            return new MyAuthoringScope();
        }
    }
}
```

## <a name="see-also"></a>См. также
- [Функции языковой службы прежних версий](../../extensibility/internals/legacy-language-service-features1.md)
- [Регистрация языковой службы прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md)
---
title: Изложение в Наследие Языковая служба (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: be485a0e7406d49c4dcce77958c720e0b62504b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706813"
---
# <a name="outlining-in-a-legacy-language-service"></a>Структурирование в языковой службе прежних версий
Изложение позволяет свернуть сложную программу в обзор или наброски. Например, в C-технологии все методы могут быть свернуты в одну строку, показывая только подпись метода. Кроме того, структуры и классы могут быть разрушены, чтобы показать только названия структур и классов. Внутри одного метода, сложная логика может быть рухнула, чтобы показать `foreach`общий поток, показывая только первую строку заявлений, таких как , `if`и `while`.

 Устаревшие языковые службы реализуются как часть VSPackage, но новый способ реализации функций языкового сервиса заключается в использовании расширений MEF. Чтобы узнать больше, смотрите [Прохождение: Изложение](../../extensibility/walkthrough-outlining.md).

> [!NOTE]
> Мы рекомендуем вам начать использовать новый API редактора как можно скорее. Это повысит производительность вашего языкового сервиса и позволит вам воспользоваться новыми функциями редактора.

## <a name="enabling-support-for-outlining"></a>Включение поддержки для обликов
 Запись `AutoOutlining` в реестр установлена на 1, чтобы включить автоматическое изложение. Автоматическое описание устанавливает разбор всего источника при загрузке или изменении файла для идентификации скрытых областей и отображания глифов. Очертания также могут управляться вручную пользователем.

 Стоимость входа `AutoOutlining` в реестр может быть <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> получена <xref:Microsoft.VisualStudio.Package.LanguagePreferences> через имущество на класс. Запись `AutoOutlining` реестра может быть инициализирована с указанным параметром <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> атрибута (подробнее см. [Регистрацию Службы языка Наследия).](../../extensibility/internals/registering-a-legacy-language-service1.md)

## <a name="the-hidden-region"></a>Скрытый регион
 Чтобы предоставить описание, ваш языковой сервис должен поддерживать скрытые регионы. Это пролеты текста, которые могут быть расширены или разрушены. Скрытые области могут быть разграничены стандартными языковыми символами, такими как фигурные скобки, или пользовательскими символами. Например, у C-е есть `#region` / `#endregion` пара, которая разграничает скрытую область.

 Скрытые регионы управляются скрытым менеджером <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> региона, который разоблачается как интерфейс.

 С изложением <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> используются скрытые области интерфейса и содержат диапазон скрытой области, текущее видимое состояние и баннер, который будет отображаться при сворачивании диапазона.

 Языковой сервис-парсер <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> использует метод для добавления нового скрытого региона <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> с поведением по умолчанию для скрытых регионов, в то время как метод позволяет настроить внешний вид и поведение контура. После того, как скрытые регионы отданы на сеанс скрытых областей, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] управляет скрытыми областями для языкового сервиса.

 Если вам нужно определить, когда будет уничтожена сессия скрытой области, изменяется скрытый регион или необходимо убедиться, что заметен определенный скрытый регион; Вы должны получить класс <xref:Microsoft.VisualStudio.Package.Source> из класса и переопределить <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A> <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A>соответствующие <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>методы, и, соответственно.

### <a name="example"></a>Пример
 Вот упрощенный пример создания скрытых областей для всех пар фигурных фигурных фигурных фигурных фигурных фигурных фигурок. Предполагается, что язык обеспечивает соответствие скобки, и что скобки, которые должны быть сопоставлены включают по крайней мере фигурные скобки (я) и No). Этот подход предназначен только для иллюстративных целей. Полная реализация будет иметь полное <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>рассмотрение дел в . В этом примере также <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> показано, как `true` временно установить предпочтение. Альтернативой является указание `AutoOutlining` указанного `ProvideLanguageServiceAttribute` параметра в атрибуте в пакете языков.

 Этот пример предполагает правила C-и для комментариев, строк и буквальных данных.

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

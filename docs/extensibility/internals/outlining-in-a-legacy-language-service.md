---
title: "Структуризация в языковую службу для прежних версий | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "структуризация"
  - "Структурирование языковые службы [платформа управляемых пакетов]"
  - "структурирование, поддержка в языковые службы [платформа управляемых пакетов]"
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Структуризация в языковую службу для прежних версий
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Структурирование позволяет свернуть сложную программу в общие сведения или структуры. Например в C\# все методы можно свернуть, чтобы одна строка, показывающая сигнатуру метода. Кроме того классы и структуры можно свернуть, чтобы отображать только имена структур и классов. В одном методе сложную логику можно свернуть, чтобы показать общий поток, показывая только первая строка инструкции, такие как `foreach`, `if`, и `while`.  
  
 Устаревший языковые службы реализуются как частью VSPackage, но это использование расширений MEF новый способ реализации возможностей службы языка. Для получения дополнительных см [Пошаговое руководство: структурирование](../../extensibility/walkthrough-outlining.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API как можно быстрее. Это улучшает производительность службы языка и позволяют воспользоваться преимуществами новых функций редактора.  
  
## Включение поддержки для структуры  
 `AutoOutlining` Запись реестра имеет значение 1, чтобы включить автоматическое структурирование. Автоматическое структурирование устанавливает анализ всего источника при загрузке или изменен для определения скрытые области и отображать структурирования переноса файла. Структурирование можно также управлять вручную пользователем.  
  
 Значение `AutoOutlining` реестра можно получить с помощью <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> свойство <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класса.`AutoOutlining` Запись реестра можно инициализировать с именованным параметром <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> атрибутов \(см. [Регистрация службы языка](../../extensibility/internals/registering-a-legacy-language-service1.md) Подробные сведения\).  
  
## Скрытые области  
 Для предоставления структурирование, службе язык должен поддерживать скрытые области. Это диапазоны текста, который можно разворачивать и сворачивать. Можно выделять скрытые области, стандартный язык символы, такие как фигурные скобки или пользовательские символы. Например, C\# имеет `#region`и`#endregion` пару, которая разделяет скрытой области.  
  
 Скрытые области управляются диспетчером скрытые области, который предоставляется как <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> интерфейса.  
  
 Структурирование использует скрытые области <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> интерфейс и содержит диапазон скрытой области, отображается текущее состояние и заголовок будет отображаться, когда диапазон свернута.  
  
 Средство синтаксического анализа языковой службы использует <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> метод для добавления новой скрытые области с поведением по умолчанию для скрытые области при <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> метод позволяет настроить внешний вид и поведение контура. После скрытой области сеанса, получают скрытые области [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] управляет скрытые области для языковой службы.  
  
 Если вам нужно определить, когда уничтожается, скрытой области сеанса, скрытой области изменяется, или необходимо убедиться, что скрытые определенного региона является видимым. необходимо создать производный класс от <xref:Microsoft.VisualStudio.Package.Source> класса и переопределить соответствующие методы <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A>, <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A>, и <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>, соответственно.  
  
### Пример  
 Ниже приведен упрощенный пример создания скрытые области для всех пар фигурные скобки. Предполагается, что язык предоставляет парные фигурные скобки и фигурные скобки для сопоставления по крайней мере включить фигурные скобки \({и}\). Этот подход является только для иллюстративных целей. Полная реализация будет иметь полный Обработка обращений в <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>. В этом примере также показано, как задать <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> предпочтение `true` временно. Альтернативным вариантом является указание `AutoOutlining` именем параметра в `ProvideLanguageServiceAttribute` атрибут в языковой пакет.  
  
 В этом примере предполагается, что правила C\# для комментариев, строк и литералы.  
  
```c#  
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
  
## См. также  
 [Компоненты прежних версий языка службы](../../extensibility/internals/legacy-language-service-features1.md)   
 [Регистрация службы языка](../../extensibility/internals/registering-a-legacy-language-service1.md)
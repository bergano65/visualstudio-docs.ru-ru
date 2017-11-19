---
title: "Структуризация в языковую службу прежних версий | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 010ec576fe8d1cd52c82165793324eede0da9e6c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/31/2017
---
# <a name="outlining-in-a-legacy-language-service"></a>Структуризация в языковую службу прежних версий
Структурирование делает возможным сворачивание сложную программу в общие сведения или структуры. Например в C# все методы можно свернуть, чтобы одна строка, показывающая сигнатуре метода. Кроме того классы и структуры можно свернуть, чтобы отображать только имена структуры и классы. В одном методе сложной логики можно свернуть, чтобы показать общий поток, отображая только первая строка инструкции, такие как `foreach`, `if`, и `while`.  
  
 Прежних версий языка службы реализованы как часть пакета VSPackage, но новой реализации возможностей службы языка можно выполнить с помощью расширений MEF. Подробнее см. в разделе [Пошаговое руководство: структурирование](../../extensibility/walkthrough-outlining.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API, как можно быстрее. Это повысит быстродействие языковой службы и позволяют воспользоваться преимуществами новых функций редактора.  
  
## <a name="enabling-support-for-outlining"></a>Включение поддержки для структуры  
 `AutoOutlining` Запись реестра имеет значение 1, чтобы включить автоматическое структурирование. Автоматическое структурирование устанавливает анализа всего источника при загрузке файла или изменить, чтобы идентифицировать скрытые области и отображать структурирования переноса. Структурирование можно также управлять вручную пользователем.  
  
 Значение `AutoOutlining` запись реестра можно получить с помощью <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> свойство <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класса. `AutoOutlining` Запись реестра можно инициализировать с именованного параметра для <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> атрибутов (см. [регистрации службы языка для прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md) подробные сведения).  
  
## <a name="the-hidden-region"></a>Скрытые области  
 Чтобы обеспечить структурирование, службе языка должен поддерживать скрытые области. Это диапазоны текста, который можно разворачивать и сворачивать. Скрытые области можно разделять символами стандартного языка, например фигурные скобки, или пользовательские символы. Например, C# имеется `#region` / `#endregion` пару, которая разделяет скрытой области.  
  
 Скрытые области управляются диспетчером скрытые области, который предоставляется как <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> интерфейса.  
  
 Структурирование использует скрытые области <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> интерфейса и содержат скрытые области, текущего состояния видимости и баннера, который будет отображаться при свернута область диапазон.  
  
 Использует средство синтаксического анализа языковой службы <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> метод, чтобы добавить новую область скрытых с поведением по умолчанию для скрытых областей, пока <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> метод позволяет настроить внешний вид и поведение контура. После сеанса скрытые области, получают скрытые области [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] управляет скрытые области в службе языка.  
  
 Если вам нужно определить, когда уничтожается скрытой области сеанса, скрытой области изменяется, или необходимо убедитесь, что скрытые определенного региона является видимым. должен быть производным от класса <xref:Microsoft.VisualStudio.Package.Source> класса и переопределить соответствующие методы <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A>, <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A>, и <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>соответственно.  
  
### <a name="example"></a>Пример  
 Ниже приведен упрощенный пример создания скрытые области для всех пар фигурные скобки. Предполагается, что язык предоставляет проверку соответствия фигурных скобок и фигурные скобки, чтобы соответствовать по крайней мере включает фигурные скобки ({и}). Этот подход является исключительно для демонстрационных целей. Полная реализация будет иметь полный обработки обращений в <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>. В этом примере также показано, как задать <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> предпочтительно `true` временно. Альтернативным вариантом является указание `AutoOutlining` с именем параметра в `ProvideLanguageServiceAttribute` атрибут языковой пакет.  
  
 В этом примере предполагается правилам языка C# для комментариев, строк и литералы.  
  
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
 [Возможности службы прежних версий языка](../../extensibility/internals/legacy-language-service-features1.md)   
 [Регистрация службы языка для прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md)
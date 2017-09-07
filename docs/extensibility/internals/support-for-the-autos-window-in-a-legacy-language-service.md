---
title: "Поддержка видимые-окно в языковую службу прежних версий | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], Autos window
- Autos window, supporting in language services [managed package framework]
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
caps.latest.revision: 12
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
ms.openlocfilehash: b6e4f4783bd4d968ad7ab4784cdd6bb32ba2392a
ms.contentlocale: ru-ru
ms.lasthandoff: 09/06/2017

---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>Поддержка видимые-окно в языковую службу прежних версий
**Видимые** окне отображаются выражения, такие как переменные и параметры, которые находятся в области видимости при приостановке отлаживаемой программы (либо из-за точки останова или исключение). Выражения могут включать переменные, локальные или глобальные и параметры, которые были изменены в локальной области. **Видимые** окна можно также включить экземпляров класса, структуры или другого типа. Все, что вычислитель выражений может вычислять потенциально могут быть отображены в **видимые** окна.  
  
 Managed package framework (MPF) не поддерживает прямой **видимые** окна. Тем не менее если необходимо переопределить <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> метод, может возвращать список выражений должны быть представлены в **видимые** окна.  
  
## <a name="implementing-support-for-the-autos-window"></a>Реализация поддержки для видимые-окно  
 Все что нужно сделать для поддержки **видимые** окно является реализация <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> метод <xref:Microsoft.VisualStudio.Package.LanguageService> класса. Такой реализации необходимо решить, заданное место в файле исходного выражения должны появиться в **видимые** окна. Метод возвращает список строк, в которых каждая строка представляет одно выражение. Возвращаемое значение <xref:Microsoft.VisualStudio.VSConstants.S_OK> указывает, что в списке содержатся выражения, а <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> указывает, что отсутствуют выражения для отображения.  
  
 Фактический выражений, возвращенных являются имена переменных или параметров, которые отображаются в этом месте в коде. Эти имена передаются в вычислителе выражений для получения значения и типы, которые затем отображаются в **видимые** окна.  
  
### <a name="example"></a>Пример  
 В следующем примере показана реализация <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> метод, который возвращает список выражений из <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> причина синтаксического анализа с помощью метода <xref:Microsoft.VisualStudio.Package.ParseReason>. Каждое из выражений, упакованная в качестве `TestVsEnumBSTR` , реализующий <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR> интерфейса.  
  
 Обратите внимание, что `GetAutoExpressionsCount` и `GetAutoExpression` методы являются методами пользовательских на `TestAuthoringSink` объекта и были добавлены для поддержки в этом примере. Они представляют один из способов какие выражения, добавляемые к `TestAuthoringSink` объекта средством синтаксического анализа (путем вызова <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A> метод) может осуществляться за пределами средство синтаксического анализа.  
  
```csharp  
using Microsoft.VisualStudio;  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        public override int GetProximityExpressions(IVsTextBuffer buffer,  
                                                    int line,  
                                                    int col,  
                                                    int cLines,  
                                                    out IVsEnumBSTR ppEnum)  
        {  
            int retval = VSConstants.E_NOTIMPL;  
            ppEnum = null;  
            if (buffer != null)  
            {  
                IVsTextLines textLines = buffer as IVsTextLines;  
                if (textLines != null)  
                {  
                    Source src = this.GetSource(textLines);  
                    if (src != null)  
                    {  
                        TokenInfo tokenInfo = new TokenInfo();  
                        string text = src.GetText();  
                        ParseRequest req = CreateParseRequest(src,  
                                                              line,  
                                                              col,  
                                                              tokenInfo,  
                                                              text,  
                                                              src.GetFilePath(),  
                                                              ParseReason.Autos,  
                                                              null);  
                        req.Scope = this.ParseSource(req);  
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;  
  
                        retval = VSConstants.S_FALSE;  
                        int spanCount = sink.GetAutoExpressionsCount();  
                        if (spanCount > 0) {  
                            TestVsEnumBSTR bstrList = new TestVsEnumBSTR();  
                            for (int i = 0; i < spanCount; i++)  
                            {  
                                TextSpan span;  
                                sink.GetAutoExpression(i, out span);  
                                string expression = src.GetText(span.iStartLine,  
                                                                span.iStartIndex,  
                                                                span.iEndLine,  
                                                                span.iEndIndex);  
                                bstrList.AddString(expression);  
                            }  
                            ppEnum = bstrList;  
                            retval = VSConstants.S_OK;  
                        }  
                    }  
                }  
            }  
            return retval;  
        }  
    }  
}  
```

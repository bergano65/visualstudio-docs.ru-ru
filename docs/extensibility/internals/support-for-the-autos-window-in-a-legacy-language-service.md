---
title: "Поддержка окно видимых переменных в языковую службу для прежних версий | Документы Microsoft"
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 88cff53ca5c335fdf60aef85d79e9c6e86f03cfa
ms.lasthandoff: 02/22/2017

---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>Поддержка окно видимых переменных в языковую службу для прежних версий
**Видимые** окне отображаются выражения, такие как переменные и параметры, которые находятся в области при приостановке отлаживаемой программы (либо из-за точки останова или исключение). Выражения могут содержать переменные, локальные или глобальные и параметры, которые были изменены в локальной области. **Видимые** окно может также включать экземпляров класса, структуры или другого типа. Все, что средство оценки выражений может вычислять потенциально могут быть отображены в **видимые** окна.  
  
 Платформа управляемых пакетов (MPF) не поддерживает прямой **видимые** окна. Тем не менее если необходимо переопределить <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A>метод, может возвращать список выражений должна присутствовать в **видимые** окно.</xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A>  
  
## <a name="implementing-support-for-the-autos-window"></a>Реализация поддержки для видимые-окно  
 Все что нужно сделать для поддержки **видимые** окна заключается в реализации <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A>метода в <xref:Microsoft.VisualStudio.Package.LanguageService>класс.</xref:Microsoft.VisualStudio.Package.LanguageService> </xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> Реализация необходимо решить, заданное место в исходном файле выражения должны появиться в **видимые** окна. Метод возвращает список строк, в которых каждая строка представляет одно выражение. Возвращаемое значение <xref:Microsoft.VisualStudio.VSConstants.S_OK>Указывает, что список содержит выражения, а <xref:Microsoft.VisualStudio.VSConstants.S_FALSE>Указывает, что никакие выражения для отображения.</xref:Microsoft.VisualStudio.VSConstants.S_FALSE> </xref:Microsoft.VisualStudio.VSConstants.S_OK>  
  
 Фактический выражений, возвращенных являются имена переменных или параметров, которые отображаются в этом месте в коде. Эти имена передаются в вычислителе выражений для получения значения и типы, которые затем отображаются в **видимые** окна.  
  
### <a name="example"></a>Пример  
 В следующем примере показана реализация <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A>метода, который возвращает список выражений из <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>метода с помощью синтаксического анализа причины <xref:Microsoft.VisualStudio.Package.ParseReason>.</xref:Microsoft.VisualStudio.Package.ParseReason> </xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> </xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> Каждое из выражений, упакованная в качестве `TestVsEnumBSTR` , реализующий <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR>интерфейса.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR>  
  
 Обратите внимание, что `GetAutoExpressionsCount` и `GetAutoExpression` методы являются пользовательские на `TestAuthoringSink` объекта и были добавлены для поддержки в этом примере. Они представляют один из способов какие выражения, добавляемые к `TestAuthoringSink` объекта анализатором (путем вызова <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A>метод) можно использовать за пределами анализатор.</xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A>  
  
```c#  
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

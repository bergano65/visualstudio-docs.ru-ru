---
title: Поддержка окна Autos в службе языка Наследия (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], Autos window
- Autos window, supporting in language services [managed package framework]
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 75f8c761721dde5dad4bb75b8675f71f678b06df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704881"
---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>Поддержка окна видимых переменных в языковой службе прежних версий
Окно **Autos** отображает такие выражения, как переменные и параметры, которые находятся в области при приостановке программы (либо из-за точки разрыва, либо из-за исключения). Выражения могут включать переменные, локальные или глобальные, а также параметры, которые были изменены в локальной области. Окно **Autos** также может включать в себя моменты класса, структуры или другого типа. Все, что может оценить оценщик выражения, потенциально может быть показано в окне **Autos.**

 Платформа управляемого пакета (MPF) не обеспечивает прямую поддержку окна **Autos.** Однако, если вы <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> переопределяете метод, вы можете вернуть список выражений, которые будут представлены в окне **Autos.**

## <a name="implementing-support-for-the-autos-window"></a>Реализация поддержки окна Авто
 Все, что вам нужно сделать для поддержки окна <xref:Microsoft.VisualStudio.Package.LanguageService> **Autos,** это реализовать <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> метод в классе. Ваша реализация должна решить, учитывая местоположение в исходном файле, какие выражения должны отображаться в окне **Autos.** Метод возвращает список строк, в которых каждая строка представляет одно выражение. Значение возврата <xref:Microsoft.VisualStudio.VSConstants.S_OK> указывает, что список содержит <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> выражения, в то время как указывает на отсутствие высыхаевых.

 Возврат фактических возвращенных выражений – это имена переменных или параметров, которые отображаются в этом месте в коде. Эти имена передаются оценщику выражения для получения значений и типов, которые затем отображаются в окне **Autos.**

### <a name="example"></a>Пример
 В следующем примере показана реализация <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> метода, который <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> получает список выражений <xref:Microsoft.VisualStudio.Package.ParseReason>из метода с помощью причины разбора. Каждое из выражений обернут `TestVsEnumBSTR` как <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR> интерфейс, который реализует интерфейс.

 Обратите внимание, что методы `GetAutoExpressionsCount` и `GetAutoExpression` `TestAuthoringSink` методы являются пользовательскими методами на объекте и были добавлены для поддержки этого примера. Они представляют собой один из способов, в котором выражения, добавленные к `TestAuthoringSink` объекту парсером (по звонку <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A> метода), могут быть доступны за пределами парсера.

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

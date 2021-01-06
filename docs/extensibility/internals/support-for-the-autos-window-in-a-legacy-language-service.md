---
title: Поддержка окна "видимые" в устаревшей языковой службе
description: Узнайте, как реализовать поддержку окна "видимые", в котором отображаются выражения, наявляющиеся в области действия при приостановке отлаживаемой программы.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: c97ab4db9b71c91689abe0afb85230e5b0242962
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/05/2021
ms.locfileid: "97876510"
---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>Поддержка окна "видимые" в устаревшей языковой службе

В окне **видимые** отображаются такие выражения, как переменные и параметры, которые находятся в области действия при приостановке отлаживаемой программы (из-за точки останова или исключения). Выражения могут включать в себя переменные, локальные или глобальные, а также параметры, измененные в локальной области. Окно **видимые** может также содержать экземпляры класса, структуры или другого типа. Все, что может вычислить средство оценки выражений, потенциально может быть показано в окне **видимые** .

 Платформа управляемого пакета (MPF) не обеспечивает прямую поддержку для окна " **видимые** ". Однако при переопределении <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> метода можно возвратить список выражений, которые должны быть представлены в окне **видимые** .

## <a name="implementing-support-for-the-autos-window"></a>Реализация поддержки для окна "видимые"

 Все, что необходимо сделать для поддержки окна **видимые** , — это реализовать <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> метод в <xref:Microsoft.VisualStudio.Package.LanguageService> классе. Ваша реализация должна принять решение, учитывая расположение в исходном файле, какие выражения должны отображаться в окне **видимые** . Метод возвращает список строк, в которых каждая строка представляет одно выражение. Возвращаемое значение <xref:Microsoft.VisualStudio.VSConstants.S_OK> указывает, что список содержит выражения, а <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> указывает, что нет выражений для отображения.

 Фактически возвращаемые выражения — это имена переменных или параметров, которые отображаются в этом месте кода. Эти имена передаются средству оценки выражений для получения значений и типов, которые затем отображаются в окне **видимые** .

### <a name="example"></a>Пример
 В следующем примере показана реализация <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> метода, который получает список выражений из <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метода, используя причину синтаксического анализа <xref:Microsoft.VisualStudio.Package.ParseReason> . Каждое из выражений упаковывается как объект `TestVsEnumBSTR` , реализующий <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR> интерфейс.

 Обратите внимание, что `GetAutoExpressionsCount` `GetAutoExpression` методы и являются пользовательскими методами `TestAuthoringSink` объекта и были добавлены для поддержки этого примера. Они представляют один из способов, с помощью которых выражения, добавляемые в `TestAuthoringSink` объект средством синтаксического анализа (путем вызова <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A> метода), доступны вне средства синтаксического анализа.

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

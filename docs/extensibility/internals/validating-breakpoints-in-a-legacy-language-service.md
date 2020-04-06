---
title: Проверка брейк-пойнтов в службе наследования языка (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af09e4f8f2156100bea9267c92ffebeb64ce1aa3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704098"
---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>Проверка точек останова в языковой службе прежних версий
Точка разрыва указывает на то, что выполнение программы должно быть прекращено в определенной точке, пока оно работает в отладчике. Пользователь может разместить точку разрыва на любой строке в исходном файле, так как редактор не знает, что представляет собой действительное место для точки разрыва. При запуске отладчика все отмеченные точки разрыва (называемые ожидающими моментов разрыва) привязаны к соответствующему местоположению в запущенной программе. В то же время точки разрыва проверяются, чтобы убедиться, что они помечают допустимые местоположения кода. Например, точка разрыва комментария недействительна, так как в этом месте нет кода в исходном коде. Отладчик отсутсвий недействительных точек разрыва.

 Поскольку языковая служба знает об отображении исходного кода, она может проверить точки разрыва до запуска отладчика. Можно переопределить <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> метод для возврата диапазона с указанием действительного местоположения для точки разрыва. Местоположение точки разрыва по-прежнему проверяется при запуске отладчика, но пользователь уведомляется о недействительных точках разрыва, не дожидаясь загрузки отладчика.

## <a name="implementing-support-for-validating-breakpoints"></a>Реализация поддержки для проверки моментов

- Методу <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> дается положение точки разрыва. Ваша реализация должна решить, является ли местоположение действительным, и указать это, вернув текстовый диапазон, который идентифицирует код, связанный с положением строки, точкой разрыва.

- Возврат, <xref:Microsoft.VisualStudio.VSConstants.S_OK> если местоположение действительно, или <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> если оно не действительно.

- Если точка разрыва действительна, то диапазон текста выделяется вместе с точкой разрыва.

- Если точка разрыва недействительна, в панели статуса появляется сообщение об ошибке.

### <a name="example"></a>Пример
 В этом примере <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> показана реализация метода, который вызывает парсер для получения промежности кода (если такового имеется) в указанном месте.

 Этот пример предполагает, что `GetCodeSpan` в <xref:Microsoft.VisualStudio.Package.AuthoringSink> класс был добавлен метод, который `true` проверяет диапазон текста и возвращается, если это допустимое местоположение точки разрыва.

```csharp
using Microsoft VisualStudio;
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    class TestLanguageService : LanguageService
    {
        public override int ValidateBreakpointLocation(IVsTextBuffer buffer,
                                                       int line,
                                                       int col,
                                                       TextSpan[] pCodeSpan)
        {
            int retval = VSConstants.S_FALSE;
            if (pCodeSpan != null)
            {
                // Initialize span to current line by default.
                pCodeSpan[0].iStartLine = line;
                pCodeSpan[0].iStartIndex = col;
                pCodeSpan[0].iEndLine = line;
                pCodeSpan[0].iEndIndex = col;
            }

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
                                                              ParseReason.CodeSpan,
                                                              null);
                        req.Scope = this.ParseSource(req);
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;

                        TextSpan span = new TextSpan();
                        if (sink.GetCodeSpan(out span))
                        {
                            pCodeSpan[0] = span;
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

## <a name="see-also"></a>См. также
- [Функции языковой службы прежних версий](../../extensibility/internals/legacy-language-service-features1.md)

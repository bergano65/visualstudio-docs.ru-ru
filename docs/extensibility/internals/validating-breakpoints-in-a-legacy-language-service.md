---
title: Проверка точек останова в языковую службу прежних версий | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 03bf1534789ba24e1bbf597874ea427057073b61
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31139381"
---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>Проверка точек останова в языковую службу прежних версий
Точка останова указывает, что остановки выполнения программы в определенный момент во время выполнения в отладчике. Пользователя можно установить точку останова в любой строке в исходном файле, поскольку редактор не имеет сведений о том, что такое является допустимым расположением точки останова. При запуске отладчика все помеченные точки останова (называемые ожидающих точек останова) привязаны соответствующее место в выполняемой программы. В то же время, которые проверяются точки останова, чтобы убедиться, что они указывают допустимый код расположения. Например точки останова на комментарий является недопустимым, поскольку нет кода в этом расположении в исходном коде. Отладчик отключает недопустимые точки останова.  
  
 Поскольку служба языка знает об отображаемых исходный код, он может проверять точки останова перед запуском отладчика. Можно переопределить <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> метод для возврата диапазон, указав допустимое расположение для точки останова. Положение точки останова по-прежнему проверяется при запуске отладчика, но пользователь получает уведомление недопустимый точек останова, не ожидая отладчика для загрузки.  
  
## <a name="implementing-support-for-validating-breakpoints"></a>Реализация поддержки для проверки точки останова  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> Метод получает позицию точки останова. Такой реализации необходимо решить ли расположение является допустимым и указать это, возвращая фрагмент текста, идентифицирующее код, связанный с номер строки точки останова.  
  
-   Вернуть <xref:Microsoft.VisualStudio.VSConstants.S_OK> Если расположение является допустимым, или <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> , если оно является недопустимым.  
  
-   Если точка останова задана в допустимый диапазон текста выделяются точки останова.  
  
-   Если точка останова является недопустимым, появится сообщение об ошибке в строке состояния.  
  
### <a name="example"></a>Пример  
 В этом примере показана реализация <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> метод, который вызывает средство синтаксического анализа, чтобы получить фрагмент кода (если таковые имеются) в указанном месте.  
  
 В этом примере предполагается, что вы добавили `GetCodeSpan` метод <xref:Microsoft.VisualStudio.Package.AuthoringSink> класс, который проверяет диапазон текста и возвращает `true` Если это расположение действительной точке останова.  
  
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
 [Возможности службы прежних версий языка](../../extensibility/internals/legacy-language-service-features1.md)
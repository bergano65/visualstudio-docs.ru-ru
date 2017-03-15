---
title: "Проверка точек останова в языковую службу для прежних версий | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
caps.latest.revision: 14
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
ms.openlocfilehash: 3a8c2df45c0a834430a499cf6a7e7ef2da10bdbf
ms.lasthandoff: 02/22/2017

---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>Проверка точек останова в языковую службу для прежних версий
Точка останова указывает, что остановки выполнения программы в определенной точке во время выполнения в отладчике. Пользователь может установить точку останова в любой строки в исходном файле, поскольку редактор не имеет сведений о того, что составляет допустимое расположение точки останова. При запуске отладчика все помеченные точки останова (называемые ожидающих точек останова) привязаны к программе, запущенной в нужном месте. В то же время, которые проверяются точки останова, чтобы убедиться, что они указывают допустимый код расположения. Например точки останова на комментарий является недопустимым, поскольку нет кода в этом расположении в исходном коде. Отладчик отключает недопустимый точки останова.  
  
 Поскольку служба языка знает об отображаемой исходный код, может проверить точки останова перед запуском отладчика. Можно переопределить <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>для возврата диапазон, указав допустимое расположение для точки останова.</xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> Точки останова по-прежнему проверяется при запуске отладчика, но пользователь получает уведомление недопустимый точек останова, не дожидаясь отладчик должен загружать.  
  
## <a name="implementing-support-for-validating-breakpoints"></a>Реализация поддержки для проверки точек останова  
  
-   <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>Метод получает позицию точки останова.</xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> Реализация необходимо решить ли расположение является допустимым и указать это, возвращая диапазон текста, который определяет код, связанный с номер строки точки останова.  
  
-   Возвращает <xref:Microsoft.VisualStudio.VSConstants.S_OK>допустимость расположение или <xref:Microsoft.VisualStudio.VSConstants.S_FALSE>, если оно является недопустимым.</xref:Microsoft.VisualStudio.VSConstants.S_FALSE> </xref:Microsoft.VisualStudio.VSConstants.S_OK>  
  
-   Если точка останова является допустимым текстовым диапазоном выделяются точки останова.  
  
-   Если точка останова является недопустимым, в строке состояния появится сообщение об ошибке.  
  
### <a name="example"></a>Пример  
 В этом примере показана реализация <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>метода, который вызывает средство синтаксического анализа для получения диапазон кода (если таковые имеются) в указанном расположении.</xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A>  
  
 Предполагается, что вы добавили `GetCodeSpan` метод <xref:Microsoft.VisualStudio.Package.AuthoringSink>класс, который проверяет диапазон текста и возвращает `true` случае точки останова допустимым.</xref:Microsoft.VisualStudio.Package.AuthoringSink>  
  
```c#  
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
 [Компоненты прежних версий языка службы](../../extensibility/internals/legacy-language-service-features1.md)

---
title: Комментирование кода синтаксиса в языковой службе прежних версий | Документация Майкрософт
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3314d27ce81e48237fa69b332b203d557d0a11d0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/22/2018
ms.locfileid: "47558325"
---
# <a name="commenting-code-in-a-legacy-language-service"></a>Комментирование кода синтаксиса в языковой службе прежних версий
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Последнюю версию этого раздела можно найти в [комментирование кода в языковой службе прежних версий](https://docs.microsoft.com/visualstudio/extensibility/internals/commenting-code-in-a-legacy-language-service).  
  
Языки программирования обычно предоставляют средства для заметок или закомментируйте код. Комментарий — это раздел текста, который предоставляет дополнительные сведения о коде, но игнорируется во время компиляции или интерпретации.  
  
 Классы управляемых пакетов framework (MPF) обеспечивают поддержку закомментирование и раскомментирование выбранного текста.  
  
## <a name="comment-styles"></a>Стили комментарий  
 Существует два общих стиля комментариев:  
  
1.  Комментарии, строки, где расположено в одной строке.  
  
2.  Комментарии блока, где комментарии могут включать несколько строк.  
  
 Строки комментариев обычно имеют начальный символ (или символы), при комментариев блоке имеют начального и конечного знаков. Например, в C# строка комментария начинается с / /, и начало комментария начинается с / * и заканчивается \*/.  
  
 Когда пользователь выбирает команду **выделенный фрагмент в комментарий** из **изменить** -> **Дополнительно** меню, команда отправляется <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> метод <xref:Microsoft.VisualStudio.Package.Source> класса. Когда пользователь выбирает команду **Раскомментировать выделенный фрагмент**, отправляется команда <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> метод.  
  
## <a name="supporting-code-comments"></a>Вспомогательные комментарии к коду  
 У вас есть комментарии язык службы поддержки кода с помощью параметра `EnableCommenting` именованный параметр из <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . Этот параметр задает <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> свойство <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класса. Дополнительные сведения о настройке языка servicce функций см. в разделе [регистрация языковой службы прежних](../../extensibility/internals/registering-a-legacy-language-service1.md)).  
  
 Необходимо также переопределить <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> метод для возврата <xref:Microsoft.VisualStudio.Package.CommentInfo> структуру с символы комментария для вашего языка. C#-по умолчанию используются символы комментария строки стиля.  
  
### <a name="example"></a>Пример  
 Ниже приведен пример реализации <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> метод.  
  
```csharp  
using Microsoft.VisualStudio.Package;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        public override CommentInfo GetCommentFormat() {  
            CommentInfo info = new CommentInfo();  
            info.LineStart       = "//";  
            info.BlockStart      = "/*";  
            info.BlockEnd        = "*/";  
            info.UseLineComments = true;  
            return info;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>См. также  
 [Функции службы устаревшего языка](../../extensibility/internals/legacy-language-service-features1.md)   
 [Регистрация языковой службы прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md)


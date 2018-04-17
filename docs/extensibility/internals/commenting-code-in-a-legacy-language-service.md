---
title: Комментирования кода в языковую службу прежних версий | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5b573b464c26c3864cece697191cf03545ada779
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
---
# <a name="commenting-code-in-a-legacy-language-service"></a>Комментирования кода в языковую службу прежних версий
Языки программирования обычно предоставляют возможность добавлять заметки или код в комментарий. Комментарий — это часть текста, который предоставляет дополнительные сведения о коде, но игнорируется во время компиляции или интерпретации.  
  
 Классы managed package framework (MPF) обеспечивают поддержку комментирования и идет раскомментирование выбранного текста.  
  
## <a name="comment-styles"></a>Стили комментария  
 Существует два общих стиля комментариев:  
  
1.  Комментарии строки, где комментария в одной строке.  
  
2.  Блок комментариев, где комментарий может включать несколько строк.  
  
 Комментарии строки обычно имеют начальный символ (или символы), при блок комментариев начального и конечного символов. Например, в C# строка комментария начинается с / /, и блочного комментария начинается с / * и заканчивается \*/.  
  
 Когда пользователь выбирает команду **выделенного фрагмента в комментарий** из **изменить** -> **Дополнительно** меню выберите команду направляется в <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> метод <xref:Microsoft.VisualStudio.Package.Source> класса. Когда пользователь выбирает команду **раскомментируйте выбора**, отправляется команда <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> метод.  
  
## <a name="supporting-code-comments"></a>Поддержка комментарии к коду  
 У вас есть комментарии языковой службы поддержки кода с помощью параметра `EnableCommenting` именованный параметр из <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . Это задает <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> свойство <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класса. Дополнительные сведения об установке компонентов servicce языка в разделе [регистрации службы языка для прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md)).  
  
 Необходимо также переопределить <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> метод для возврата <xref:Microsoft.VisualStudio.Package.CommentInfo> структуру с символы комментария для выбранного языка. C#-по умолчанию используются символы комментария стиль строки.  
  
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
 [Возможности службы прежних версий языка](../../extensibility/internals/legacy-language-service-features1.md)   
 [Регистрация службы языка для прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md)
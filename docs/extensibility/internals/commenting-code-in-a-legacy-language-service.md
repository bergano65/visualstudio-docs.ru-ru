---
title: Комментирование кода синтаксиса в языковой службе прежних версий | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9f6b7796ff4bd8f2b37e50e53d58de66f823ef8a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/21/2019
ms.locfileid: "56639665"
---
# <a name="comment-code-in-a-legacy-language-service"></a>Комментарий кода в языковой службы прежних версий
Языки программирования обычно предоставляют средства для заметок или закомментируйте код. Комментарий — это раздел текста, который предоставляет дополнительные сведения о коде, но игнорируется во время компиляции или интерпретации.

 Классы управляемых пакетов framework (MPF) обеспечивают поддержку закомментирование и раскомментирование выбранного текста.

## <a name="comment-styles"></a>Стили комментарий
Существует два общих стиля комментариев:

1.  Комментарии, строки, где расположено в одной строке.

2.  Комментарии блока, где комментарии могут включать несколько строк.


Строки комментариев обычно имеют начальный символ (или символы), при комментариев блоке имеют начального и конечного знаков. Например, в C# строка комментария начинается с `//`, и начало комментария начинается с `/*` и заканчивается `*/`.

Когда пользователь выбирает команду **выделенный фрагмент в комментарий** из **изменить** > **Дополнительно** меню, команда отправляется <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> метод <xref:Microsoft.VisualStudio.Package.Source> класса. Когда пользователь выбирает команду **Раскомментировать выделенный фрагмент**, отправляется команда <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> метод.

## <a name="support-code-comments"></a>Комментарии к коду поддержки
 У вас есть комментарии язык службы поддержки кода с помощью параметра `EnableCommenting` именованный параметр из <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . Этот параметр задает <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> свойство <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класса. Дополнительные сведения о настройке языка функции службы, см. в разделе [регистрация языковой службы прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md).

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
- [Функции службы устаревшего языка](../../extensibility/internals/legacy-language-service-features1.md)
- [Регистрация языковой службы прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md)
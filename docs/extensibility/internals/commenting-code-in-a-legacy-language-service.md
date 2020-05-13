---
title: Комментарий Кода в Службе Языка Наследия (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5450199fde29f581dafdf9b2884c88ef26ea4ce7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709440"
---
# <a name="comment-code-in-a-legacy-language-service"></a>Комментарий к коду в устаревшей языковой службе
Языки программирования обычно предоставляют средства для аннотирования или комментария кода. Комментарий представляет собой раздел текста, который предоставляет дополнительную информацию о коде, но игнорируется во время компиляции или интерпретации.

 Классы управляемых пакетов (MPF) обеспечивают поддержку для комментирования и некомментируть выбранный текст.

## <a name="comment-styles"></a>Стили комментариев
Есть два общих стиля комментариев:

1. Комментарии строки, где комментарий находится на одной строке.

2. Блокируйте комментарии, где комментарий может включать несколько строк.

Комментарии строки обычно имеют исходный символ (или символы), в то время как комментарии блоков имеют как начальные, так и конечные символы. Например, в C' комментарий строки начинается с `//` `/*` , и `*/`комментарий блока начинается с и заканчивается с .

Когда пользователь выбирает **выбор комментариев** команды из меню **Edit** > **Advanced,** <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> команда направляется в метод <xref:Microsoft.VisualStudio.Package.Source> в классе. Когда пользователь выбирает команду **Uncomment Selection,** команда направляется <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> в метод.

## <a name="support-code-comments"></a>Комментарии к коду поддержки
 Вы можете иметь свой код службы `EnableCommenting` языковой поддержки с помощью указанного параметра <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . Это устанавливает <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> свойство <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класса. Для получения дополнительной информации об настройке функций языкового сервиса можно [ознакомиться на устаревшей языковой службе.](../../extensibility/internals/registering-a-legacy-language-service1.md)

 Необходимо также переопределить <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> метод возврата <xref:Microsoft.VisualStudio.Package.CommentInfo> структуры с символами комментариев для вашего языка. Символы комментариев в стиле C'-стиль являются по умолчанию.

### <a name="example"></a>Пример
 Вот пример реализации <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> метода.

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
- [Функции устаревшего языкового сервиса](../../extensibility/internals/legacy-language-service-features1.md)
- [Регистрация устаревшей языковой службы](../../extensibility/internals/registering-a-legacy-language-service1.md)

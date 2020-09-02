---
title: Комментирование кода в языковой службе прежних версий | Документация Майкрософт
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cd1405456ca9a6ba00926c82bcc7959ea36d26c2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160909"
---
# <a name="commenting-code-in-a-legacy-language-service"></a>Комментирование кода синтаксиса в языковой службе прежних версий
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Языки программирования обычно предоставляют средства для добавления заметок или комментирования кода. Комментарий — это раздел текста, содержащий дополнительные сведения о коде, но пропускаемый во время компиляции или интерпретации.  
  
 Классы Managed Package Framework (MPF) обеспечивают поддержку комментирования и раскомментирования выделенного текста.  
  
## <a name="comment-styles"></a>Стили комментариев  
 Существует два общих стиля комментариев:  
  
1. Комментарии строки, где комментарий находится в одной строке.  
  
2. Блокировать комментарии, в которых комментарий может включать несколько строк.  
  
   Комментарии в строках обычно имеют начальный символ (или символы), а в комментариях к блокам — начальные и конечные символы. Например, в C# строчный комментарий начинается с//, а блок комментария начинается с/* и заканчивается на \* /.  
  
   Когда пользователь выбирает командный **Комментарий** в меню **Правка**  ->  **Дополнительно** , команда направляется к <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> методу <xref:Microsoft.VisualStudio.Package.Source> класса. Когда пользователь выбирает команду **раскомментировать выделенный фрагмент**, команда направляется в <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> метод.  
  
## <a name="supporting-code-comments"></a>Поддержка комментариев к коду  
 Языковая служба может поддерживать комментарии кода с помощью `EnableCommenting` именованного параметра <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . При этом задается <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> свойство <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класса. Дополнительные сведения о настройке функций языка сервикце см. [в разделе Регистрация устаревшей языковой службы](../../extensibility/internals/registering-a-legacy-language-service1.md).  
  
 Также необходимо переопределить метод, <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> чтобы он возвращал <xref:Microsoft.VisualStudio.Package.CommentInfo> структуру с символами комментария для вашего языка. Символы комментария строки в стиле C# используются по умолчанию.  
  
### <a name="example"></a>Пример  
 Ниже приведен пример реализации <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> метода.  
  
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
  
## <a name="see-also"></a>См. также:  
 [Функции устаревшей языковой службы](../../extensibility/internals/legacy-language-service-features1.md)   
 [Регистрация языковой службы прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md)

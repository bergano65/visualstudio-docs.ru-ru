---
title: "Комментирование кода в языковую службу для прежних версий | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "комментарии, поддержка в языковые службы [платформа управляемых пакетов]"
  - "комментирование кода языковые службы [платформа управляемых пакетов]"
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Комментирование кода в языковую службу для прежних версий
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Языки программирования обычно предоставляют средства аннотации и прокомментировать код.  Комментарий раздел текст, который содержит дополнительные сведения о коде, однако не обрабатывается во время компиляции или интерпретации.  
  
 Управляемые классы платформы пакета \(MPF\) предоставляют поддержку для комментариев и uncommenting выделенный текст.  
  
## Стили комментария  
 2 Общих стиля комментариев:  
  
1.  Комментарии линии, где комментарий на одной линии.  
  
2.  Комментарии блока, где комментарий может включать несколько линий.  
  
 Комментарии линии обычно имеют \(начальный символ или символы\), а комментарии блока имеют знаков начала и завершения.  Например, в c\# комментарий линии начинается с \/\/и с комментария начинается и заканчивается с блока\/\* \*\/.  
  
 Когда пользователь выбирает команду **Преобразовать выделенный фрагмент в комментарий** от  **изменить** \- \>  **Дополнительно** меню выберите команду перенаправляется  <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> метод  <xref:Microsoft.VisualStudio.Package.Source> класс.  Когда пользователь выбирает команду **Отменить преобразование в комментарий**команда направлялась  <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> метод.  
  
## Поддержка комментарии к коду  
 Можно использовать комментарии кода поддержки языка посредством `EnableCommenting` параметр  <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> .  При этом устанавливаются <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> свойство   <xref:Microsoft.VisualStudio.Package.LanguagePreferences> класс.  Дополнительные сведения о функциях языка servicce параметра см. в разделе [Регистрация службы языка](../../extensibility/internals/registering-a-legacy-language-service1.md)\).  
  
 Также необходимо переопределить <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> метод, чтобы он возвращал a  <xref:Microsoft.VisualStudio.Package.CommentInfo> структура с символами комментария для выбранного языка.  Символы комментария линии в стиле значение по умолчанию.  
  
### Пример  
 Здесь реализация примера  <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> метод.  
  
```c#  
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
  
## См. также  
 [Компоненты прежних версий языка службы](../../extensibility/internals/legacy-language-service-features1.md)   
 [Регистрация службы языка](../../extensibility/internals/registering-a-legacy-language-service1.md)
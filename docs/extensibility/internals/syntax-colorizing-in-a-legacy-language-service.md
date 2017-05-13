---
title: "Синтаксис выделения цветом в языковую службу для прежних версий | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
caps.latest.revision: 28
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: b9d98323b3957108746b22702306c9155b142fb9
ms.contentlocale: ru-ru
ms.lasthandoff: 02/22/2017

---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>Синтаксис выделения цветом в языковую службу для прежних версий
Цветовая разметка синтаксиса-функция вызывает различные элементы языка программирования, отображаемый в исходном файле, в различные цвета и стили. Для поддержки этой возможности, необходимо указать средство синтаксического анализа или сканер, который можно определить типы лексические элементы или маркеры в файле. Многие языки различать ключевые слова, разделители (например, круглые или фигурные скобки) и комментарии по выделения цветом, их по-разному.  
  
 Устаревший языковые службы реализуются как частью VSPackage, но это использование расширений MEF новый способ реализации возможностей службы языка. Для получения дополнительных см [расширение редактора и языковые службы](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API как можно быстрее. Это улучшает производительность службы языка и позволяют воспользоваться преимуществами новых функций редактора.  
  
## <a name="implementation"></a>Реализация  
 Для поддержки выделение цветом, платформа управляемых пакетов (MPF) включает <xref:Microsoft.VisualStudio.Package.Colorizer>класса, который реализует интерфейс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>интерфейс.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> </xref:Microsoft.VisualStudio.Package.Colorizer> Этот класс взаимодействует с <xref:Microsoft.VisualStudio.Package.IScanner>для определения цвета и маркер.</xref:Microsoft.VisualStudio.Package.IScanner> Дополнительные сведения о сканеры см [синтаксического анализа службы языка прежних версий и сканера](../../extensibility/internals/legacy-language-service-parser-and-scanner.md). <xref:Microsoft.VisualStudio.Package.Colorizer>Класс затем помечает каждый символ маркера с помощью информации о цвете и возвращает эту информацию в редактор исходного файла отображения.</xref:Microsoft.VisualStudio.Package.Colorizer>  
  
 Цвет сведения, возвращаемые в редактор — это индекс в списке цветных элементов. Каждый цветного элемента указывает значение цвета и набор атрибутов шрифта, такие как полужирный шрифт или зачеркивания. Редактор предоставляет набор по умолчанию цветных элементов, которые могут использовать службы языка. Нужно всего лишь указать индекс соответствующий цвет для каждого типа маркера. Тем не менее можно предоставить набор пользовательских цветные элементы и индексы, которые вводятся для маркеров и собственный список ссылок на цветных элементов вместо списка по умолчанию. Необходимо также установить `RequestStockColors` запись реестра на 0 (или не указывайте `RequestStockColors` запись вообще) для поддержки пользовательских цветов. Можно задать этот параметр реестра с именованным параметром <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>пользовательского атрибута.</xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Дополнительные сведения о регистрации языковой службы и его параметров в разделе [регистрация языковую службу для прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md).  
  
## <a name="custom-colorable-items"></a>Пользовательские цветных элементов  
 Чтобы предоставить свои собственные пользовательские цветных элементов, необходимо переопределить <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A>и <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A>метод для <xref:Microsoft.VisualStudio.Package.LanguageService>класса.</xref:Microsoft.VisualStudio.Package.LanguageService> </xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> </xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> Первый метод возвращает число пользовательских цветных элементов, поддерживаемых службой языка и второй возвращает пользовательский цветного элемента по индексу. Создать список пользовательских цветных элементов по умолчанию. В конструкторе службы языка все, что необходимо сделать, — указать каждый цветного элемента с именем. Visual Studio автоматически обрабатывает случай, когда пользователь выбирает другой набор цветных элементов. Это имя является то, что будет отображаться в **шрифты и цвета** страницу свойств на **параметры** диалоговое окно (доступные из Visual Studio **средства** меню) и это имя определяет, какой цвет, когда пользователь переопределил. Выборы пользователя хранятся в кэше в реестре и доступен по имени цвета. **Шрифты и цвета** свойство странице перечислены названия цветов в алфавитном порядке, пользовательских цветов можно группировать, перед именем каждого цвета название языка, например, «**TestLanguage - комментарий**«и»**TestLanguage - ключевое слово**». Или можно группировать цветных элементов по типу, «**комментария (TestLanguage)**«и»**ключевое слово (TestLanguage)**». Группирование по имени языка является предпочтительным.  
  
> [!CAUTION]
>  Настоятельно рекомендуется включить имя языка в имя цветного элемента, чтобы избежать конфликтов с существующими именами цветного элемента.  
  
> [!NOTE]
>  Если изменить имя одного из цветов во время разработки, необходимо сбросить кэша, при первом запуске цвета невозможен, созданную Visual Studio. Это можно сделать, запустив **Сбросить экспериментальный куст** из меню программы Visual Studio SDK.  
  
 Обратите внимание, никогда не ссылаться на первый элемент в списке цветных элементов. Visual Studio предоставляет всегда цвета текста по умолчанию и атрибуты этого элемента. Самым простым способом работы с этим является предоставить заполнитель цветного элемента как первый элемент.  
  
### <a name="high-color-colorable-items"></a>High Color цветных элементов  
 Цветные элементы также могут поддерживать значения цвета 24 бита или высоким через <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>интерфейса.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> MPF <xref:Microsoft.VisualStudio.Package.ColorableItem>поддерживает класс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>интерфейс и 24-разрядных цветов задаются в конструкторе, а также обычные цвета.</xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> </xref:Microsoft.VisualStudio.Package.ColorableItem> В разделе <xref:Microsoft.VisualStudio.Package.ColorableItem>класс для получения дополнительных сведений.</xref:Microsoft.VisualStudio.Package.ColorableItem> В приведенном ниже примере показано, как задать цвета 24 бита для ключевых слов и комментариев. 24-разрядных цветов используются при 24-разрядный цвет поддерживается на рабочем столе пользователя; в ином случае используются цвета обычный текст.  
  
 Помните, что это цвета по умолчанию для вашего языка; пользователь может изменить эти цвета на все, что захотят.  
  
### <a name="example"></a>Пример  
 В этом примере показан способ объявления и заполнить массив пользовательских цветных элементов с помощью <xref:Microsoft.VisualStudio.Package.ColorableItem>класса.</xref:Microsoft.VisualStudio.Package.ColorableItem> В этом примере задает ключевое слово и комментарий цветов, с использованием 24-разрядных цветов.  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    public class TestLanguageService : LanguageService  
    {  
        private ColorableItem[] m_colorableItems;  
  
        TestLanguageService() : base()  
        {  
            m_colorableItems = new ColorableItem[] {  
                new ColorableItem("TestLanguage - Text",  
                                  "Text",  
                                  COLORINDEX.CI_SYSPLAINTEXT_FG,  
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,  
                                  System.Drawing.Color.Empty,  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_DEFAULT),  
                new ColorableItem("TestLanguage - Keyword",  
                                  "Keyword",  
                                  COLORINDEX.CI_MAROON,  
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,  
                                  System.Drawing.Color.FromArgb(192,32,32),  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_BOLD),  
                new ColorableItem("TestLanguage - Comment",  
                                  "Comment",  
                                  COLORINDEX.CI_DARKGREEN,  
                                  COLORINDEX.CI_LIGHTGRAY,  
                                  System.Drawing.Color.FromArgb(32,128,32),  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_DEFAULT)  
                // ...  
                // Add as many colorable items as you want to support.  
            };  
        }  
    }  
}  
```  
  
## <a name="the-colorizer-class-and-the-scanner"></a>Класс Colorizer и сканером  
 Базовый <xref:Microsoft.VisualStudio.Package.LanguageService>класс имеет <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A>метод <xref:Microsoft.VisualStudio.Package.Colorizer>класса</xref:Microsoft.VisualStudio.Package.Colorizer> , instantiantes</xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> </xref:Microsoft.VisualStudio.Package.LanguageService> Сканер, который возвращается из <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>методу передается <xref:Microsoft.VisualStudio.Package.Colorizer>конструктора класса.</xref:Microsoft.VisualStudio.Package.Colorizer> </xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>  
  
 Необходимо реализовать <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>метод в версии <xref:Microsoft.VisualStudio.Package.LanguageService>класса.</xref:Microsoft.VisualStudio.Package.LanguageService> </xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> <xref:Microsoft.VisualStudio.Package.Colorizer>Класс использует сканер получить всю информацию о цвете маркера.</xref:Microsoft.VisualStudio.Package.Colorizer>  
  
 Сканер должен заполнить <xref:Microsoft.VisualStudio.Package.TokenInfo>структуры для каждого маркера, он находит.</xref:Microsoft.VisualStudio.Package.TokenInfo> Эта структура содержит информацию, например диапазон маркера занимает индекс цвета, какой тип имеет триггеры маркеров и маркеров (см. <xref:Microsoft.VisualStudio.Package.TokenTriggers>).</xref:Microsoft.VisualStudio.Package.TokenTriggers> Необходимые только индекс диапазона и цвет окраски <xref:Microsoft.VisualStudio.Package.Colorizer>класса.</xref:Microsoft.VisualStudio.Package.Colorizer>  
  
 Цветовой индекс хранится в <xref:Microsoft.VisualStudio.Package.TokenInfo>структуры обычно представляет собой значение из <xref:Microsoft.VisualStudio.Package.TokenColor>перечисления, который предоставляет несколько именованных индексов, соответствующий различных элементов языка, таких как операторы и ключевые слова.</xref:Microsoft.VisualStudio.Package.TokenColor> </xref:Microsoft.VisualStudio.Package.TokenInfo> Если ваш пользовательский цветных элементов списка соответствует элементы представлены в <xref:Microsoft.VisualStudio.Package.TokenColor>перечисления, то можно просто использовать перечисление качестве цвета для каждого маркера.</xref:Microsoft.VisualStudio.Package.TokenColor> Однако при наличии дополнительных цветных элементов или не хотите использовать существующие значения в указанном порядке, можно упорядочить список пользовательских цветных элементов в соответствии с потребностями и возвращать соответствующий индекс в списке. Просто убедитесь, что приведение к <xref:Microsoft.VisualStudio.Package.TokenColor>индекса при хранении в структуре <xref:Microsoft.VisualStudio.Package.TokenInfo>; [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] видит только индекс.</xref:Microsoft.VisualStudio.Package.TokenInfo> </xref:Microsoft.VisualStudio.Package.TokenColor>  
  
### <a name="example"></a>Пример  
 В следующем примере показано, как средство проверки можно определить три типа маркера: числа, знаки препинания и идентификаторы (все, что не является числом или знаки препинания). Этот пример является только в иллюстративных целях и не представляет полную реализацию синтаксического анализа и проверки. Предполагается, что существует `Lexer` класса `GetNextToken()` метод, который возвращает строку.  
  
```c#  
using Microsoft.VisualStudio.Package;  
using Microsoft.VisualStudio.TextManager.Interop;  
  
namespace TestLanguagePackage  
{  
    private Lexer lex;  
  
    public class TestScanner : IScanner  
    {  
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,  
                                                   ref int state)  
        {  
            bool foundToken = false;  
            string token = lex.GetNextToken();  
            if (token != null)  
            {  
                char firstChar = token[0];  
                if (Char.IsPunctuation(firstChar))  
                {  
                    tokenInfo.Type = TokenType.Operator;  
                    tokenInfo.Color = TokenColor.Keyword;  
                }  
                else if (Char.IsNumber(firstChar))  
                {  
                    tokenInfo.Type = TokenType.Literal;  
                    tokenInfo.Color = TokenColor.Number;  
                }  
                else  
                {  
                    tokenInfo.Type = TokenType.Identifier;  
                    tokenInfo.Color = TokenColor.Identifier;  
                }  
            }  
            return foundToken;  
        }  
```  
  
## <a name="see-also"></a>См. также  
 [Компоненты прежних версий языка службы](../../extensibility/internals/legacy-language-service-features1.md)   
 [Средство синтаксического анализа языка прежних версий службы и сканера](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)   
 [Регистрация службы языка для прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md)

---
title: Цветовая маркировка синтаксиса в языковой службе прежних версий | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ba516701ec232cb49edfee9888625789b544d62
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/25/2019
ms.locfileid: "54948652"
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>Цветовая маркировка синтаксиса в языковой службе прежних версий
Цветовое выделение синтаксиса — это функция, которое вызывает различные элементы языка программирования для отображения в исходном файле в различные цвета и стили. Для поддержки этой возможности, необходимо предоставить синтаксического анализатора или сканера, можно определять типы лексические элементы или токены в файл. Многие языки различать ключевые слова, разделители (например, круглых или фигурных скобок) и комментарии по выделения цветом их по-разному.  
  
 Устаревший языковой службы реализуются как часть пакета VSPackage, но новый способ реализовать функции языковой службы является использование расширений MEF. Дополнительные сведения см. в разделе [расширение редактора и языковых служб](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API как можно скорее. Это улучшит производительность службы языка и позволяют воспользоваться преимуществами новых функций редактора.  
  
## <a name="implementation"></a>Реализация  
 Для поддержки Раскраска, managed package framework (MPF) включает <xref:Microsoft.VisualStudio.Package.Colorizer> класса, который реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> интерфейс. Этот класс взаимодействует с <xref:Microsoft.VisualStudio.Package.IScanner> для определения маркера и цвета. Дополнительные сведения о сканеры, см. в разделе [средства синтаксического анализа службы языка для прежних версий и сканер](../../extensibility/internals/legacy-language-service-parser-and-scanner.md). <xref:Microsoft.VisualStudio.Package.Colorizer> Класс помечает каждый символ токена с сведения о цвете и затем возвращает эту информацию в редактор, отображающий исходный файл.  
  
 Сведения о цвете, возвращается в редактор — это индекс в список цветных элементов. Указывает каждого цветного элемента, значение цвета и набор атрибутов шрифта, такие как полужирный или зачеркиванием. Редактор добавляет набор по умолчанию цветных элементов, которые могут использовать службы вашего языка. Вам нужно всего лишь указать индекс соответствующий цвет для каждого типа маркера. Тем не менее можно предоставить набор пользовательских цветных элементов и индексов, которое вы указали для маркеров и ссылаются на собственный список цветных элементов, а не список по умолчанию. Необходимо также задать `RequestStockColors` запись реестра до 0 (или не указывайте `RequestStockColors` во все) для поддержки пользовательских цветов. Можно задать этот параметр реестра с помощью именованного параметра <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> пользовательского атрибута. Дополнительные сведения о регистрации языковой службы и настройка его параметров, см. в разделе [регистрация языковой службы прежних](../../extensibility/internals/registering-a-legacy-language-service1.md).  
  
## <a name="custom-colorable-items"></a>Настраиваемые цветные элементы  
 Для предоставления собственных пользовательских цветных элементов, необходимо переопределить <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> и <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> метод <xref:Microsoft.VisualStudio.Package.LanguageService> класса. Первый метод возвращает количество пользовательских цветных элементов, поддерживаемых службой языка, а второй возвращает настраиваемого цветного элемента по индексу. Создается по умолчанию список пользовательских цветных элементов. В конструкторе класса службы языка все, что нужно сделать, — указать каждого цветного элемента с именем. Visual Studio автоматически обрабатывает случай, когда пользователь выбирает другой набор цветных элементов. Это имя отображается в **шрифты и цвета** страницу свойств на **параметры** диалоговое окно (доступные из Visual Studio **средства** меню) и определяет, какие это имя цвет пользователь переопределен. Выборы пользователя хранятся в кэше в реестре и доступен по имени цвета. **Шрифты и цвета** свойство странице перечислены названия цветов в алфавитном порядке, чтобы их можно группировать пользовательские цвета, отделяя каждое имя цвета на название языка; например, "**TestLanguage - комментарий**«и»**TestLanguage - ключевое слово**«. Или можно сгруппировать цветных элементов по типу, "**комментария (TestLanguage)**«и»**ключевое слово (TestLanguage)**«. Группирование по имени языка является предпочтительным.  
  
> [!CAUTION]
>  Настоятельно рекомендуется включить имя языка в имя цветного элемента, чтобы избежать конфликтов с существующими именами цветного элемента.  
  
> [!NOTE]
>  Если изменить имя одного цветов во время разработки, необходимо сбросить кэш, созданную Visual Studio в первый раз обращается к цвета. Это можно сделать, выполнив **Сбросить экспериментальный куст** команду в меню программы Visual Studio SDK.  
  
 Обратите внимание на то, что первый элемент в список цветных элементов никогда не указывается. Visual Studio всегда предоставляет цвета текста по умолчанию и атрибуты этого элемента. Самый простой способ работы с этим является для предоставления цветного элемента заполнителя как первый элемент.  
  
### <a name="high-color-colorable-items"></a>High Color цветных элементов  
 Цветные элементы также могут поддерживать значения цвета 24-разрядный или высокого уровня с помощью <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> интерфейс. MPF <xref:Microsoft.VisualStudio.Package.ColorableItem> поддерживает класс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> интерфейс и цвета 24-разрядный задаются в конструкторе, а также обычные цвета. Дополнительные сведения см. в описании класса <xref:Microsoft.VisualStudio.Package.ColorableItem>. В приведенном ниже примере показано, как задать цвета 24 бит для ключевых слов и комментариев. Цвета 24 бита используются в том случае, когда 24-разрядный цвет поддерживается на рабочем столе пользователя; в противном случае используются цвета обычного текста.  
  
 Помните, что это цвета по умолчанию для вашего языка; пользователь может изменить эти цвета, чтобы все, что захотят.  
  
### <a name="example"></a>Пример  
 В этом примере показан один способ объявления и заполнить массив пользовательских цветных элементов с помощью <xref:Microsoft.VisualStudio.Package.ColorableItem> класса. В этом примере задает ключевое слово и комментарий цветов, с помощью цвета 24 бита.  
  
```csharp  
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
  
## <a name="the-colorizer-class-and-the-scanner"></a>Класс палитры и сканера  
 Базовый <xref:Microsoft.VisualStudio.Package.LanguageService> класс имеет <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> метод этого instantiantes <xref:Microsoft.VisualStudio.Package.Colorizer> класса. Средство проверки, который возвращается из <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> методу передается <xref:Microsoft.VisualStudio.Package.Colorizer> конструктора класса.  
  
 Необходимо реализовать <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> метод в собственную версию <xref:Microsoft.VisualStudio.Package.LanguageService> класса. <xref:Microsoft.VisualStudio.Package.Colorizer> Класс использует сканер для получения всех сведений цвет маркера.  
  
 Средство проверки необходимо заполнять <xref:Microsoft.VisualStudio.Package.TokenInfo> структуры для каждого маркера он находит. Эта структура содержит сведения, такие как диапазон маркера занимает цветовой индекс, какой тип является триггеры маркера и маркером (см. в разделе <xref:Microsoft.VisualStudio.Package.TokenTriggers>). Только индекс диапазона и цвет необходимы для окраски, <xref:Microsoft.VisualStudio.Package.Colorizer> класса.  
  
 Цветовой индекс хранится в <xref:Microsoft.VisualStudio.Package.TokenInfo> структура обычно представляет собой значение из <xref:Microsoft.VisualStudio.Package.TokenColor> перечисления, который предоставляет ряд именованных индексов, соответствующих для различных элементов языка, например ключевых слов и операторов. Если ваш пользовательских цветных элементов списка соответствий элементы представлены в <xref:Microsoft.VisualStudio.Package.TokenColor> перечисления, то можно просто использовать перечисление качестве цвета для каждого токена. Тем не менее если у вас есть дополнительные цветных элементов, или вы не хотите использовать существующие значения в указанном порядке, можно упорядочить список пользовательских цветных элементов, в соответствии с потребностями и возвращать соответствующий индекс в этом списке. Убедитесь, что для приведения индекс <xref:Microsoft.VisualStudio.Package.TokenColor> при хранении в <xref:Microsoft.VisualStudio.Package.TokenInfo> структуры; [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] видит только индекс.  
  
### <a name="example"></a>Пример  
 В следующем примере показано, как средство проверки может определить три типа маркера: цифры, знаки препинания и идентификаторы (все, что не является числом или знаки препинания). В этом примере — только в иллюстративных целях и не представляет комплексное средство синтаксического анализа и сканер реализации. Предполагается, что имеется `Lexer` класса `GetNextToken()` метод, который возвращает строку.  
  
```csharp  
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
 [Функции службы устаревшего языка](../../extensibility/internals/legacy-language-service-features1.md)   
 [Средство синтаксического анализа устаревший языковой службы и средства проверки](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)   
 [Регистрация языковой службы прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md)
---
title: "Синтаксис Раскраска в языковую службу прежних версий | Документы Microsoft"
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
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 1ec6732b511d437a24149d9cd4b20e593a13a8f0
ms.contentlocale: ru-ru
ms.lasthandoff: 09/06/2017

---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>Синтаксис Раскраска в языковую службу прежних версий
Синтаксис Раскраска-функция вызывает различных элементов языка программирования, отображаемый в файле исходного кода в различных цветов и стилей. Для поддержки этой возможности, необходимо указать средство синтаксического анализа или сканер, можно определить, какие типы лексические элементы или токены в файл. Многие языки различать ключевые слова, разделители (например, круглые или фигурные скобки) и комментарии по Раскраска их по-разному.  
  
 Прежних версий языка службы реализованы как часть пакета VSPackage, но новой реализации возможностей службы языка можно выполнить с помощью расширений MEF. Подробнее см. в разделе [расширение редактора и языковые службы](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API, как можно быстрее. Это повысит быстродействие языковой службы и позволяют воспользоваться преимуществами новых функций редактора.  
  
## <a name="implementation"></a>Реализация  
 Для поддержки выделение цветом, managed package framework (MPF) включает <xref:Microsoft.VisualStudio.Package.Colorizer> класса, который реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> интерфейса. Этот класс взаимодействует с <xref:Microsoft.VisualStudio.Package.IScanner> для определения маркера и цвета. Дополнительные сведения о сканеры см. в разделе [средство синтаксического анализа службы языка для прежних версий и сканера](../../extensibility/internals/legacy-language-service-parser-and-scanner.md). <xref:Microsoft.VisualStudio.Package.Colorizer> Класса помечает каждый символ маркер цвет шрифта и затем возвращает эту информацию в редактор, отображающий файл источника.  
  
 Цвет шрифта, возвращается к редактору — это индекс в списке цветных элементов. Каждого цветного элемента задает значение цвета и набор атрибутов шрифта, такие как полужирный или зачеркивания. Редактор предоставляет набор по умолчанию цветных элементов, которые могут использовать службы языка. Вам нужно всего лишь указать индекс соответствующий цвет для каждого типа маркера. Тем не менее можно предоставить набор пользовательских цветные элементы и индексы, которые вводятся для маркеров и ссылаются на собственный список цветных элементов вместо списка по умолчанию. Необходимо также задать `RequestStockColors` запись реестра до 0 (или не указывайте `RequestStockColors` запись вообще) для поддержки пользовательских цветов. Можно задать этот параметр реестра с именованного параметра для <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> пользовательского атрибута. Дополнительные сведения о регистрации языковой службы и настройка его параметров см. в разделе [регистрации службы языка для прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md).  
  
## <a name="custom-colorable-items"></a>Цветные настраиваемые элементы  
 Чтобы предоставить свои собственные пользовательские цветных элементов, необходимо переопределить <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> и <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> метод <xref:Microsoft.VisualStudio.Package.LanguageService> класса. Первый метод возвращает число пользовательских цветных элементов, поддерживаемых службой языка и второй возвращает пользовательского окрашиваемого элемента по индексу. Создания пользовательских цветных элементов списка по умолчанию. В конструкторе языковой службы все, что нужно сделать, — указать каждого цветного элемента с именем. Visual Studio автоматически обрабатывает случай, когда пользователь выбирает другой набор цветных элементов. Это имя является то, что будет отображаться в **шрифты и цвета** страницу свойств на **параметры** диалоговое окно (доступные из Visual Studio **средства** меню) и определяет, какой это имя цвет пользователь переопределен. Пользовательские настройки хранятся в кэше в реестре и доступен по имени цвета. **Шрифты и цвета** свойство странице перечислены названия цветов в алфавитном порядке, пользовательских цветов можно группировать, перед именем каждого цвета с вашим именем языка; например, «**TestLanguage комментариев**«и»**TestLanguage - ключевое слово**». Или можно сгруппировать вашей цветных элементов по типу, "**комментария (TestLanguage)**«и»**ключевое слово (TestLanguage)**». Группирование по имени языка является предпочтительным.  
  
> [!CAUTION]
>  Настоятельно рекомендуется включать имя языка, в имени цветного элемента, чтобы избежать конфликтов с существующими именами цветного элемента.  
  
> [!NOTE]
>  Если изменить имя одного из цветов во время разработки, необходимо сбросить кэш, созданным цвета невозможен, при первом запуске Visual Studio. Это можно сделать, запустив **Сбросить экспериментальный куст** команды в меню программы Visual Studio SDK.  
  
 Обратите внимание, что первый элемент в списке цветные элементы никогда не указывается. Visual Studio предоставляет всегда цвета текста по умолчанию и атрибуты этого элемента. Самым простым способом при этом — предоставить заполнитель цветного элемента как первый элемент.  
  
### <a name="high-color-colorable-items"></a>Цветные элементы High Color  
 Цветные элементы также могут поддерживать значения цвета 24-разрядный или высокого уровня через <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> интерфейса. MPF <xref:Microsoft.VisualStudio.Package.ColorableItem> поддерживает класс <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> интерфейс и 24-разрядных цветов указанный в конструкторе вместе с обычные цвета. Дополнительные сведения см. в описании класса <xref:Microsoft.VisualStudio.Package.ColorableItem>. В приведенном ниже примере показано, как задать цвета 24-разрядный для ключевых слов и комментариев. 24-разрядных цветов будут использоваться при 24-разрядный цвет поддерживается на рабочем столе пользователя; в противном случае используются цвета обычного текста.  
  
 Помните, что это цвета по умолчанию для своего языка; пользователь может изменить эти цвета на все, что захотят.  
  
### <a name="example"></a>Пример  
 В этом примере показано, как объявить и заполнить массив пользовательских цветных элементов с помощью <xref:Microsoft.VisualStudio.Package.ColorableItem> класса. В этом примере задает ключевое слово и комментарий цветов, с использованием 24-разрядных цветов.  
  
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
  
## <a name="the-colorizer-class-and-the-scanner"></a>Класс Colorizer и сканера  
 Базовый <xref:Microsoft.VisualStudio.Package.LanguageService> класс имеет <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> метод, instantiantes <xref:Microsoft.VisualStudio.Package.Colorizer> класса. Сканер, которое возвращается из <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> методу передается <xref:Microsoft.VisualStudio.Package.Colorizer> конструктора класса.  
  
 Необходимо реализовать <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> метод в собственную версию <xref:Microsoft.VisualStudio.Package.LanguageService> класса. <xref:Microsoft.VisualStudio.Package.Colorizer> Класс использует сканер для получения всех маркеров цвет шрифта.  
  
 Необходимо заполнить сканер <xref:Microsoft.VisualStudio.Package.TokenInfo> структуры для каждого маркера он находит. Эта структура содержит информацию, например диапазон маркер занимает индекс цвета, какой тип имеет триггеры токена и токена (см. <xref:Microsoft.VisualStudio.Package.TokenTriggers>). Только индекс находится в диапазоне и цвет необходимы окраски по <xref:Microsoft.VisualStudio.Package.Colorizer> класса.  
  
 Цветовой индекс хранится в <xref:Microsoft.VisualStudio.Package.TokenInfo> структура обычно представляет собой значение из <xref:Microsoft.VisualStudio.Package.TokenColor> перечисления, который предоставляет ряд именованных индексов, соответствующих для различных элементов языка, например слов и операторов. Если ваш пользовательский цветные элементы списка соответствий элементов представлены в <xref:Microsoft.VisualStudio.Package.TokenColor> перечисления, то можно просто использовать перечисление цвет для каждого токена. Если у вас есть дополнительные цветные элементы или вы не хотите использовать существующие значения в указанном порядке, вы можете упорядочить список пользовательских цветные элементы в соответствии с потребностями и возвращать соответствующий индекс в списке. Просто убедитесь, что для приведения к индекса <xref:Microsoft.VisualStudio.Package.TokenColor> при хранении в <xref:Microsoft.VisualStudio.Package.TokenInfo> структуры; [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] видит только индекс.  
  
### <a name="example"></a>Пример  
 В следующем примере показано, как средство проверки можно определить три типа маркера: цифры, знаки пунктуации и идентификаторы (все, что не является числом или знаки препинания). Данный пример является исключительно для демонстрационных целей и не представляет комплексное средство синтаксического анализа и сканер реализации. Предполагается, что имеется `Lexer` класса `GetNextToken()` метод, который возвращает строку.  
  
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
 [Возможности службы прежних версий языка](../../extensibility/internals/legacy-language-service-features1.md)   
 [Средство синтаксического анализа языка прежних версий службы и сканера](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)   
 [Регистрация службы языка для прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md)

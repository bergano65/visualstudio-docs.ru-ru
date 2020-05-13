---
title: Синтаксис окраски в наследие языковой службы (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 02723a09254255b98291cb921ae5ec091d8b9859
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704705"
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>Цветовая маркировка синтаксиса в языковой службе прежних версий
Окраска Syntax — это функция, которая приводит к отображению различных элементов языка программирования в исходном файле в разных цветах и стилях. Для поддержки этой функции необходимо предоставить парсер или сканер, который может идентифицировать типы лексических элементов или токенов в файле. Многие языки различают ключевые слова, делимитеры (например, скобки или скобки) и комментарии, раскрашивая их по-разному.

 Устаревшие языковые службы реализуются как часть VSPackage, но новый способ реализации функций языкового сервиса заключается в использовании расширений MEF. Чтобы узнать больше, смотрите [Расширение редактора и языковых служб](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Мы рекомендуем вам начать использовать новый API редактора как можно скорее. Это повысит производительность вашего языкового сервиса и позволит вам воспользоваться новыми функциями редактора.

## <a name="implementation"></a>Реализация
 Для поддержки окраски в структуру управляемого <xref:Microsoft.VisualStudio.Package.Colorizer> пакета (MPF) входит класс, который реализует <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> интерфейс. Этот класс взаимодействует <xref:Microsoft.VisualStudio.Package.IScanner> с токеном и цветами. Для получения дополнительной информации о сканерах, см [Наследие Языковая служба Parser и сканер](../../extensibility/internals/legacy-language-service-parser-and-scanner.md). Затем <xref:Microsoft.VisualStudio.Package.Colorizer> класс помечает каждый символ маркера информацией о цвете и возвращает эту информацию редактору, отображая исходный файл.

 Цветовая информация, возвращенная редактору, представляет собой индекс в список цветных элементов. Каждый цветной элемент определяет цветовое значение и набор атрибутов шрифта, таких как смелый или ударный. Редактор поставляет набор цветных элементов по умолчанию, которые может использовать языковая служба. Все, что вам нужно сделать, это указать соответствующий индекс цвета для каждого типа маркера. Тем не менее, вы можете предоставить набор пользовательских цветных элементов и индексов, которые вы поставляете для токенов, и ссылку на свой собственный список цветных элементов вместо списка по умолчанию. Вы также должны `RequestStockColors` установить запись реестра на `RequestStockColors` 0 (или не указать запись на всех) для поддержки пользовательских цветов. Эту запись реестра можно установить с <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> указанным параметром для пользовательского атрибута. Для получения дополнительной информации о регистрации языковой службы и настройке ее возможностей [см.](../../extensibility/internals/registering-a-legacy-language-service1.md)

## <a name="custom-colorable-items"></a>Настраиваемые цветные элементы
 Чтобы поставить свои собственные предметы, пригодные <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> для <xref:Microsoft.VisualStudio.Package.LanguageService> окраски, необходимо переопределить <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> и метод в классе. Первый метод возвращает количество пользовательских цветных элементов, которые поддерживает языковая служба, а второй получает пользовательский цветной элемент по индексу. Вы создаете список пользовательских цветных элементов по умолчанию. В конструкторе вашего языкового сервиса все, что вам нужно сделать, это предоставить каждый цветной элемент с именем. Visual Studio автоматически обрабатывает случай, когда пользователь выбирает другой набор цветных элементов. Это имя — это то, что отображается на странице свойств **шрифтов и цветов** в диалоговом поле **Options** (доступно из меню Visual Studio **Tools),** и это имя определяет, какой цвет пользователь переопределил. Выбор пользователя хранится в кэше в реестре и доступен по имени цвета. Страница свойств **шрифтов и цветов** перечисляет все названия цветов в алфавитном порядке, так что вы можете сгруппировать пользовательские цвета, предшествуя каждому имени цвета с вашим именем языка; например, "**TestLanguage-Комментарий**" и "**TestLanguage- Ключевое слово**". Или вы можете сгруппировать свои цветные предметы по типу, "**Комментарий (TestLanguage)**" и "**Ключевое слово (TestLanguage)**". Предпочтительна группировка по имени языка.

> [!CAUTION]
> Настоятельно рекомендуется включить имя языка в имя товара, чтобы избежать столкновений с существующими цветными именами элементов.

> [!NOTE]
> Если вы измените имя одного из цветов во время разработки, необходимо сбросить кэш, созданный Visual Studio при первом доступе к вашим цветам. Вы можете сделать это, запустив команду **«Экспериментальный улей»** из меню программы Visual Studio SDK.

 Обратите внимание, что первый элемент в списке цветных элементов никогда не упоминается. Visual Studio всегда поставляет цвета текста по умолчанию и атрибуты для этого элемента. Самый простой способ борьбы с этим заключается в поставке заполнителя цветной пункт в качестве первого пункта.

### <a name="high-color-colorable-items"></a>Высокоцветные предметы
 Цветные элементы могут также поддерживать 24-битные <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> или высокие значения цвета через интерфейс. Класс MPF <xref:Microsoft.VisualStudio.Package.ColorableItem> поддерживает <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> интерфейс, а 24-битные цвета указаны в конструкторе вместе с обычными цветами. Дополнительные сведения см. в описании класса <xref:Microsoft.VisualStudio.Package.ColorableItem>. Приведенный ниже пример показывает, как установить 24-битные цвета для ключевых слов и комментариев. 24-битные цвета используются при поддержке 24-битного цвета на рабочем столе пользователя; в противном случае используются обычные цвета текста.

 Помните, что это цвета по умолчанию для вашего языка; пользователь может изменить эти цвета на все, что они хотят.

### <a name="example"></a>Пример
 В этом примере показан один из способов декларирования <xref:Microsoft.VisualStudio.Package.ColorableItem> и заполнения массива пользовательских цветных элементов с помощью класса. Этот пример устанавливает ключевые слова и комментарии цвета с помощью 24-битных цветов.

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

## <a name="the-colorizer-class-and-the-scanner"></a>Класс Colorizer и сканер
 Базовый <xref:Microsoft.VisualStudio.Package.LanguageService> класс <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> имеет метод, который <xref:Microsoft.VisualStudio.Package.Colorizer> мгновенно ускоряет класс. Сканер, который возвращается <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> из метода, передается конструктору <xref:Microsoft.VisualStudio.Package.Colorizer> класса.

 Метод необходимо <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> реализовать в своей <xref:Microsoft.VisualStudio.Package.LanguageService> версии класса. Класс <xref:Microsoft.VisualStudio.Package.Colorizer> использует сканер для получения всей информации о цвете маркеров.

 Сканер должен заполнить структуру <xref:Microsoft.VisualStudio.Package.TokenInfo> для каждого найденного маркера. Эта структура содержит информацию, такую как диапазон, который занимает маркер, цветной индекс для использования, <xref:Microsoft.VisualStudio.Package.TokenTriggers>какой тип маркера, и триггеры маркера (см.). Для окраски <xref:Microsoft.VisualStudio.Package.Colorizer> классом необходимы только диапазон и цветовой индекс.

 Цветовой индекс, <xref:Microsoft.VisualStudio.Package.TokenInfo> хранящийся в <xref:Microsoft.VisualStudio.Package.TokenColor> структуре, обычно является значением из перечисления, которое обеспечивает ряд названных индексов, соответствующих различным языковым элементам, таким как ключевые слова и операторы. Если пользовательский список цветных элементов <xref:Microsoft.VisualStudio.Package.TokenColor> соответствует элементам, представленным в перечислении, то вы можете просто использовать перечисление в качестве цвета для каждого маркера. Однако, если у вас есть дополнительные цветные элементы или вы не хотите использовать существующие значения в этом порядке, вы можете организовать свой пользовательский список цветных элементов в соответствии с вашими потребностями и вернуть соответствующий индекс в этот список. Просто не забудьте бросить <xref:Microsoft.VisualStudio.Package.TokenColor> индекс при хранении <xref:Microsoft.VisualStudio.Package.TokenInfo> его в структуре; [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] видит только индекс.

### <a name="example"></a>Пример
 В следующем примере показано, как сканер может определить три типа маркеров: числа, знаки препинания и идентификаторы (все, что не является числом или пунктуацией). Этот пример предназначен только для иллюстративных целей и не представляет собой всеобъемлющего парцера и реализации сканера. Он предполагает, что `Lexer` есть класс `GetNextToken()` с методом, который возвращает строку.

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
- [Функции языковой службы прежних версий](../../extensibility/internals/legacy-language-service-features1.md)
- [Средство синтаксического анализа и сканер языковой службы прежних версий](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
- [Регистрация языковой службы прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md)

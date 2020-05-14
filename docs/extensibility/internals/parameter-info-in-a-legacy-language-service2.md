---
title: Информация о параметрах в Справочнике Наследия2 (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Parameter Info tool tip
- language services [managed package framework], IntelliSense Parameter Info
- Parameter Info (IntelliSense), supporting in language services [managed package framework]
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e2c40c9ca5c038a70714545f4133db0c0dd686d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706750"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Сведения о параметрах в языковой службе прежних версий
Информация о параметре IntelliSense — это инструмент, который отображает подпись метода при найме пользователя начального символа списка параметров (обычно открытая скобка) для списка параметров метода. По мере ввода каждого параметра и набраны параметры сепаратора (обычно запятой), набор инструментов обновляется, чтобы показать следующий параметр жирным шрифтом.

 Классы управляемых пакетов (MPF) обеспечивают поддержку для управления набором инструментов Parameter Info. Парсер должен определить запуск параметра, следующий параметр и конечные символы параметра, а также предоставить список подписей метода и связанные с ними параметры.

 Устаревшие языковые службы реализуются как часть VSPackage, но новый способ реализации функций языкового сервиса заключается в использовании расширений MEF. Чтобы узнать больше, смотрите [Расширение редактора и языковых служб](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Мы рекомендуем вам начать использовать новый API редактора как можно скорее. Это повысит производительность вашего языкового сервиса и позволит вам воспользоваться новыми функциями редактора.

## <a name="implementation"></a>Реализация
 Парсер должен установить <xref:Microsoft.VisualStudio.Package.TokenTriggers> значение триггера устанавливается, когда он находит параметр список начального символа (часто открытый скобки). Он должен <xref:Microsoft.VisualStudio.Package.TokenTriggers> установить спусковой крючок, когда он находит параметр сепаратора (часто запятая). Это приводит к обновлению инструмента Параметр Инфо и отобрадению следующего параметра жирным шрифтом. Парсер должен установить <xref:Microsoft.VisualStudio.Package.TokenTriggers> триггерное значение, когда, если находит конечный символ списка параметров (часто близкий скобки).

 Значение <xref:Microsoft.VisualStudio.Package.TokenTriggers> триггера инициирует <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> вызов к методу, который, в свою очередь, вызывает <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> парсер метода с причиной <xref:Microsoft.VisualStudio.Package.ParseReason>разбора. Если парсер определяет, что идентификатор перед символом запуска списка параметров является признанным <xref:Microsoft.VisualStudio.Package.AuthoringScope> именем метода, он возвращает список подписей метода сопоставления в объекте. Если какие-либо подписи метода были найдены, инструмент параметр Info отображается с первой подписью в списке. Этот набор инструментов затем обновляется по мере набранной дополнительной подписи. При найме конечного символа списка параметров из представления удаляется набор инструментов «Парамфофоф».

> [!NOTE]
> Чтобы убедиться, что набор инструментов Parameter Info правильно отформатирован, необходимо переопределить свойства <xref:Microsoft.VisualStudio.Package.Methods> в классе, чтобы предоставить соответствующие символы. Базовый <xref:Microsoft.VisualStudio.Package.Methods> класс предполагает подпись метода c'-style. Ознакомьтесь с классом, <xref:Microsoft.VisualStudio.Package.Methods> чтобы узнать о том, как это можно сделать.

## <a name="enabling-support-for-the-parameter-info"></a>Включение поддержки информации о параметрах
 Для поддержки параметра Info tooltips необходимо установить указанный `ShowCompletion` <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> параметр. `true` Языковая служба считывает значение этой <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> записи реестра из собственности.

 Кроме того, <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> свойство должно `true` быть установлено для отображаемого инструмента Параметр Инфо.

### <a name="example"></a>Пример
 Вот упрощенный пример обнаружения символов списка параметров и настройки соответствующих триггеров. Этот пример предназначен только для иллюстративных целей. Предполагается, что ваш сканер `GetNextToken` содержит метод, который идентифицирует и возвращает токены из строки текста. Пример кода просто устанавливает триггеры всякий раз, когда он видит правильный вид символа.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestScanner : IScanner
    {
        private Lexer lex;
        private const char parameterListStartChar = '(';
        private const char parameterListEndChar   = ')';
        private const char parameterNextChar      = ',';

        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false
            string token = lex.GetNextToken();
            if (token != null)
            {
                foundToken = true;
                char c = token[0];
                if (Char.IsPunctuation(c))
                {
                    tokenInfo.Type = TokenType.Operator;
                    tokenInfo.Color = TokenColor.Keyword;
                    tokenInfo.EndIndex = index;

                    if (c == parameterListStartChar)
                    {
                        tokenInfo.Trigger |= TokenTriggers.ParameterStart;
                    }
                    else if (c == parameterListNextChar)
                    {
                        tokenInfo.Trigger |= TokenTriggers.ParameterNext;
                    else if (c == parameterListEndChar)
                    {
                        tokenInfo.Trigger |= TokenTriggers.ParameterEnd;
                    }
                }
            return foundToken;
        }
    }
}
```

## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>Поддержка Параметр Информация ToolTip в Parser
 Класс <xref:Microsoft.VisualStudio.Package.Source> делает некоторые предположения о <xref:Microsoft.VisualStudio.Package.AuthoringScope> содержании <xref:Microsoft.VisualStudio.Package.AuthoringSink> и классах при отображении и обновлении инструмента Parameter Info.

- Парсер дается <xref:Microsoft.VisualStudio.Package.ParseReason> при наведанном персонаже стартового списка параметров.

- Место, данное <xref:Microsoft.VisualStudio.Package.ParseRequest> в объекте, происходит сразу после начала параметра. Парсер должен собрать подписи всех методологий деклараций, доступных в этой позиции, и хранить их в списке в вашей версии <xref:Microsoft.VisualStudio.Package.AuthoringScope> объекта. Этот список включает имя метода, тип метода (или тип возврата) и список возможных параметров. Позже этот список ищется для подписи или подписи метода для отображения в наборе инструментов Parameter Info.

  Затем парсер должен разобрать линию, <xref:Microsoft.VisualStudio.Package.ParseRequest> указанную объектом, чтобы собрать имя вводимого метода, а также то, как далеко пользователь находится в параметрах ввода. Это достигается путем передачи имени <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> метода <xref:Microsoft.VisualStudio.Package.AuthoringSink> методу на <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> объекте, а затем вызова метода при <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> разборе символа запуска списка параметров, вызова <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> метода при разборе списка параметров следующего символа и, наконец, вызова метода при разборе конечного символа списка параметров. Результаты этих вызовов метода <xref:Microsoft.VisualStudio.Package.Source> используются классом для правильного обновления инструментария Параметр Инфо.

### <a name="example"></a>Пример
 Вот строка текста, в который может ввести пользователь. Цифры ниже линии указывают, какой шаг делается парсером в этом положении в строке (при условии разбора движений слева направо). Предположение здесь состоит в том, что все перед строкой уже было разогнано для сигнатуры метода, включая подпись метода «testfunc».

```
testfunc("a string",3);
     ^^          ^ ^
     12          3 4
```

 Шаги, которые принимает парсер, изложены ниже:

1. Парсер звонит <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> с текстом "testfunc".

2. Парсер вызывает <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>.

3. Парсер вызывает <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>.

4. Парсер вызывает <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>.

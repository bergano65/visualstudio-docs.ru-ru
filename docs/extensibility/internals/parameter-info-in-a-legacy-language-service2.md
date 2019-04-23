---
title: Сведения о параметрах в языковой службы прежних версий2 | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Parameter Info tool tip
- language services [managed package framework], IntelliSense Parameter Info
- Parameter Info (IntelliSense), supporting in language services [managed package framework]
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 838e057fd0063df6a1c592dfefee759b56b9f89b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/22/2019
ms.locfileid: "60041199"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Сведения о параметрах в языковой службе прежних версий
Сведения о параметрах IntelliSense — tooltip, отображающий сигнатура метода, когда пользователь вводит в списке параметров начального символа (обычно открывающей круглой скобкой) для списка параметров метода. Каждый параметр вводится и имеет тип разделителя параметра (обычно запятой), подсказка обновляется для отображения следующего параметра полужирным шрифтом.

 Классы управляемых пакетов framework (MPF) поддерживает управление сведения о параметрах всплывающей подсказки. Средство синтаксического анализа определяется, параметр запуска, параметр рядом, и параметр конечных символов и его необходимо указать список сигнатур методов и связанными с ними параметрами.

 Устаревший языковой службы реализуются как часть пакета VSPackage, но новый способ реализовать функции языковой службы является использование расширений MEF. Дополнительные сведения см. в разделе [расширение редактора и языковых служб](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API как можно скорее. Это улучшит производительность службы языка и позволяют воспользоваться преимуществами новых функций редактора.

## <a name="implementation"></a>Реализация
 Средство синтаксического анализа следует задать значение триггера <xref:Microsoft.VisualStudio.Package.TokenTriggers> устанавливается при обнаружении начального символа параметр списка (часто открывающая скобка). Она должна задать <xref:Microsoft.VisualStudio.Package.TokenTriggers> активировать при нахождении разделителя параметров (часто запятая). В этом случае сведения о параметрах всплывающей подсказки для обновления и отображения следующего параметра полужирным шрифтом. Средство синтаксического анализа следует задать значение триггера <xref:Microsoft.VisualStudio.Package.TokenTriggers> при если находит конечный символ списка параметров (часто закрывающая круглая скобка).

 <xref:Microsoft.VisualStudio.Package.TokenTriggers> Значение триггера инициирует вызов <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> метод, который в свою очередь вызывает <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> средство синтаксического анализа метод синтаксического анализа причину <xref:Microsoft.VisualStudio.Package.ParseReason>. Если средство синтаксического анализа определяет, что перед списком параметров начального символа идентификатора является именем распознанных метод, он возвращает список сопоставлении сигнатур методов в <xref:Microsoft.VisualStudio.Package.AuthoringScope> объекта. Если найдены все подписи метода, сведения о параметрах всплывающей подсказки отображается с подписью, первой в списке. Этой подсказкой обновляется, как введено несколько подписи. При вводе конечный символ списка параметров, сведения о параметрах всплывающей подсказки удаляется из представления.

> [!NOTE]
>  Чтобы убедиться, что сведения о параметрах всплывающей подсказки имеет правильный формат, необходимо переопределить свойства на <xref:Microsoft.VisualStudio.Package.Methods> классе, чтобы предоставить соответствующие символы. Базовый <xref:Microsoft.VisualStudio.Package.Methods> предполагается, что класс C#-стиль сигнатуру метода. См. в разделе <xref:Microsoft.VisualStudio.Package.Methods> класс Дополнительные сведения о том, как это можно сделать.

## <a name="enabling-support-for-the-parameter-info"></a>Включение поддержки для сведения о параметрах
 Для поддержки сведения о параметрах подсказки, необходимо задать `ShowCompletion` именованный параметр из <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> для `true`. Языковая служба считывает значение этой записи реестра из <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> свойство.

 Кроме того <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> свойству должно быть присвоено `true` для подсказки, сведения о параметрах для отображения.

### <a name="example"></a>Пример
 Ниже приведен упрощенный пример того, обнаружение символов списка параметров и установив соответствующие триггеры. Данный пример является только для иллюстративных целей. Предполагается, что сканер содержит метод `GetNextToken` идентификации и возвращает токены из строки текста. В примере кода просто задает триггеры, при каждом обнаружении правильный тип символа.

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

## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>Поддержка подсказке сведений о параметрах в средстве синтаксического анализа
 <xref:Microsoft.VisualStudio.Package.Source> Класс делает некоторые предположения о содержимом <xref:Microsoft.VisualStudio.Package.AuthoringScope> и <xref:Microsoft.VisualStudio.Package.AuthoringSink> классов при отображается и обновить сведения о параметрах всплывающей подсказки.

- Получает средство синтаксического анализа <xref:Microsoft.VisualStudio.Package.ParseReason> когда вводится знак начала списка параметров.

- Расположение, указанное <xref:Microsoft.VisualStudio.Package.ParseRequest> объект находится сразу после списка параметров начального символа. Средство синтаксического анализа необходимо собрать все подписи всех объявлений методов, доступных в позицию и сохранить их в список в вашей версии <xref:Microsoft.VisualStudio.Package.AuthoringScope> объекта. Этот список содержит имя метода, метод типа (или тип возвращаемого значения), а также список возможных параметров. Этот список позже поиск сигнатуры метода или подписи для отображения в подсказке сведения о параметрах.

  Средство синтаксического анализа необходимо затем выполнять синтаксический анализ строки, определяемое <xref:Microsoft.VisualStudio.Package.ParseRequest> объект для получения имени метода ввода, а также насколько оно Продвинулось пользователь находится в ввода параметров. Это достигается путем передачи имени метода для <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> метод <xref:Microsoft.VisualStudio.Package.AuthoringSink> объекта и затем вызвать <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> анализируется метод, когда список параметров начального символа, вызвав <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> метод при список параметров Следующий символ является проанализированные и наконец вызывающий <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> метод при синтаксическом анализе конечный символ списка параметров. Результаты вызовов этого метода используются <xref:Microsoft.VisualStudio.Package.Source> класс соответствующим образом обновить сведения о параметрах всплывающей подсказки.

### <a name="example"></a>Пример
 Вот строка текста, которые может ввести пользователь. Числа ниже этой линии указывают на каком этапе берется средством синтаксического анализа в этой позиции в строке (при условии, что синтаксического анализа перемещается слева направо). Здесь предполагается, что все, что перед строкой уже было проанализировано для сигнатур методов, включая сигнатуру метода «testfunc».

```
testfunc("a string",3);
     ^^          ^ ^
     12          3 4
```

 Ниже описаны шаги, которые средство синтаксического анализа принимает:

1. Вызывает средство синтаксического анализа <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> с текстом «testfunc».

2. Вызывает средство синтаксического анализа <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>.

3. Вызывает средство синтаксического анализа <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>.

4. Вызывает средство синтаксического анализа <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>.
---
title: "Сведения о параметрах в прежних версий языка Service2 | Документы Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IntelliSense, Parameter Info tool tip
- language services [managed package framework], IntelliSense Parameter Info
- Parameter Info (IntelliSense), supporting in language services [managed package framework]
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
caps.latest.revision: "23"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 69c65fa2691f71b3bb7f115b771a0de83d543f03
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/22/2017
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Сведения о параметрах в языковую службу прежних версий
Сведения о параметре IntelliSense — всплывающую подсказку, которая отображает подпись метода, когда пользователь вводит в списке параметров начальный знак (обычно открывающая скобка) для списка параметров метода. Каждый параметр вводится и типизированные разделителя параметра (обычно запятую), подсказка обновляется для отображения следующего параметра полужирным шрифтом.  
  
 Классы managed package framework (MPF) обеспечивают поддержку управления всплывающая подсказка о параметрах. Средство синтаксического анализа необходимо определить параметр запуска, параметр рядом, и знаки завершения параметра и его необходимо указать список сигнатур методов и их связанные параметры.  
  
 Прежних версий языка службы реализованы как часть пакета VSPackage, но новой реализации возможностей службы языка можно выполнить с помощью расширений MEF. Подробнее см. в разделе [расширение редактора и языковые службы](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API, как можно быстрее. Это повысит быстродействие языковой службы и позволяют воспользоваться преимуществами новых функций редактора.  
  
## <a name="implementation"></a>Реализация  
 Средство синтаксического анализа следует задать значение триггера <xref:Microsoft.VisualStudio.Package.TokenTriggers> устанавливается при обнаружении символ начала списка параметра (часто открывающая скобка). Он должен устанавливать <xref:Microsoft.VisualStudio.Package.TokenTriggers> триггер при нахождении разделителя параметров (обычно запятую). В этом случае сведения о параметрах всплывающей подсказки и Показать следующего параметра полужирным шрифтом. Средство синтаксического анализа следует задать значение триггера <xref:Microsoft.VisualStudio.Package.TokenTriggers> при если находит знак окончания списка параметров (часто закрывающая круглая скобка).  
  
 <xref:Microsoft.VisualStudio.Package.TokenTriggers> Значение триггера инициирует вызов <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> метод, который в свою очередь вызывает <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> метод синтаксического анализа причину синтаксического анализа <xref:Microsoft.VisualStudio.Package.ParseReason>. Если средство синтаксического анализа определяет, что идентификатор перед списком параметров начальный знак не является распознанным именем метода, то возвращается список совпадающих сигнатуры метода в <xref:Microsoft.VisualStudio.Package.AuthoringScope> объекта. Если обнаружены сигнатур метода, первой подписи в списке отображается всплывающая подсказка о параметрах. Эту подсказку обновляется по более подписи набора. При вводе символ окончания списка параметра подсказка о параметрах удаляется из представления.  
  
> [!NOTE]
>  Чтобы обеспечить подсказка о параметрах имеет правильный формат, необходимо переопределить свойства на <xref:Microsoft.VisualStudio.Package.Methods> класса для предоставления соответствующих символов. Базовый <xref:Microsoft.VisualStudio.Package.Methods> предполагается класса C#-стиль сигнатуру метода. В разделе <xref:Microsoft.VisualStudio.Package.Methods> класса сведения о том, как это сделать.  
  
## <a name="enabling-support-for-the-parameter-info"></a>Включение поддержки для сведения о параметре  
 Для поддержки подсказки о параметрах, необходимо задать `ShowCompletion` именованный параметр из <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> для `true`. Языковая служба считывает значение этой записи реестра из <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> свойство.  
  
 Кроме того <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> свойству необходимо присвоить значение `true` для подсказки, сведения о параметрах для отображения.  
  
### <a name="example"></a>Пример  
 Ниже приведен упрощенный пример того, какие символы списка параметров и установив соответствующие триггеры. Данный пример является исключительно для демонстрационных целей. Предполагается, что сканер содержит метод `GetNextToken` , определяет и возвращает токенов из текстовой строки. В примере кода просто устанавливает триггеры при каждом обнаружении правильный тип символа.  
  
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
  
## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>Поддержка Info параметра всплывающей подсказки в средстве синтаксического анализа  
 <xref:Microsoft.VisualStudio.Package.Source> Класса делает некоторые предположения о содержимом <xref:Microsoft.VisualStudio.Package.AuthoringScope> и <xref:Microsoft.VisualStudio.Package.AuthoringSink> классов при отображается всплывающая подсказка о параметрах и обновлены.  
  
-   Получает средство синтаксического анализа <xref:Microsoft.VisualStudio.Package.ParseReason> при типизированных знак начала списка параметров.  
  
-   Расположение, заданное в <xref:Microsoft.VisualStudio.Package.ParseRequest> объект находится сразу после списка параметров начального символа. Средство синтаксического анализа необходимо собрать все подписи всех объявлений методов в положение и сохранять их в список в вашей версии <xref:Microsoft.VisualStudio.Package.AuthoringScope> объекта. Этот список включает имя метода, метод типа (или тип возвращаемого значения) и список возможных параметров. Этот список позднее поиск сигнатуры метода или подписи будет отображаться в подсказке сведения о параметрах.  
  
 Средство синтаксического анализа необходимо затем выполнять синтаксический анализ строки, заданные <xref:Microsoft.VisualStudio.Package.ParseRequest> объект для сбора имя метода, который вводится, а также насколько вдоль пользователя находится в ввода параметров. Это достигается путем передачи имени метода, <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> метод <xref:Microsoft.VisualStudio.Package.AuthoringSink> объекта и затем вызвать <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> проанализировать метод, если список параметров запуска символ вызова <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> метод при список параметров Следующий символ синтаксического анализа и наконец вызов метода <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> метод при синтаксическом анализе знак окончания списка параметров. Результаты этих вызовов метода используются <xref:Microsoft.VisualStudio.Package.Source> класс, чтобы соответствующим образом обновить сведения о параметрах всплывающей подсказки.  
  
### <a name="example"></a>Пример  
 Вот строка текста, которые пользователь может ввести. Числа ниже этой линии указывают на каком этапе берется средством синтаксического анализа в этой позиции в строке (при условии, что синтаксического анализа перемещается слева направо). Здесь предполагается, что все данные перед строкой уже проверен для подписи методов, включая сигнатура метода «testfunc».  
  
```  
testfunc("a string",3);  
     ^^          ^ ^  
     12          3 4  
```  
  
 Действия, средство синтаксического анализа принимает представлены ниже:  
  
1.  Средство синтаксического анализа вызовов <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> с текстом «testfunc».  
  
2.  Вызывает средство синтаксического анализа <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>.  
  
3.  Вызывает средство синтаксического анализа <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>.  
  
4.  Вызывает средство синтаксического анализа <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>.
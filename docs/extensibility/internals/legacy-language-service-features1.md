---
title: "Features1 устаревших языковой службы | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "языковые службы [платформа управляемых пакетов]"
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Компоненты прежних версий языка службы
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Управляемая служба языка платформы пакета \(MPF\) может поддерживать один или несколько [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] функции, например выделение синтаксиса, технологией IntelliSense и проверка точки останова.  Каждая функция может быть базовым независимым других но требуют средства синтаксического анализа и средства чтения за исключением выделения синтаксиса, который требуется только средства чтения.  
  
## В этом подразделе  
 [Проверка парности фигурных скобок в языковую службу для прежних версий](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
 Описывает, что требуется для поддержки соответствовать языковых пары, также известный как проверка парности фигурных скобок.  
  
 [Комментирование кода в языковую службу для прежних версий](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
 Описывает, что требуется для поддержки комментарий и uncommenting выбранного кода.  
  
 [Пользовательские свойства документа в языковую службу для прежних версий](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
 Описывает, что требуется для поддержки свойств документа, внедренных в файле источника.  
  
 [Структуризация в языковую службу для прежних версий](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
 Описывает, что требуется для поддержки структурирование через реализацию скрытых областей.  
  
 [Форматирование кода в языковую службу для прежних версий](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
 Описывает, что требуется для поддержки переформатирование код.  
  
 [Поддержка фрагментов кода в языковую службу для прежних версий](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
 Описывает, что требуется для поддержки фрагменты кода, сегменты кода, которые вставляются и могут редактироваться.  
  
 [Сведения о параметрах в языковую службу для прежних версий](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
 Описывает, что требуется для поддержки операции IntelliSense для отображения сведений о параметрах подписи методов как метод типизирован.  
  
 [Краткие сведения в языковую службу для прежних версий](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
 Описывает, что требуется для поддержки информационную операции IntelliSense быструю для отображения сведений об идентификаторе.  
  
 [Завершение члена в языковую службу для прежних версий](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
 Описывает, что требуется для поддержки операции завершения IntelliSense для элемента выбрать член пространства имен из списка.  
  
 [Завершение слов в языковую службу для прежних версий](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
 Описывает, что необходимо для машинного слов IntelliSense поддерживает операцию для выполнения полной частично типизированные машинные слова.  
  
 [Поддержка окно видимых переменных в языковую службу для прежних версий](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
 Описывает, что служба языка может сделать для поддержки **Видимые** окно во время отладки.  
  
 [Поддержка панели навигации в языковую службу для прежних версий](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
 Описывает использование **Панель переходов** в верхней части представления редактора для реализации быстрый переход любой тип или член в файле, указанном в этом представлении.  
  
 [Синтаксис выделения цветом в языковую службу для прежних версий](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
 Описывает, что требуется для поддержки выбора синтаксиса исходного кода.  
  
 [Проверка точек останова в языковую службу для прежних версий](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
 Описывает, что служба языка может сделать для поддержки проверять точки останова вне отладчика.  
  
## Связанные подразделы  
 [Средство синтаксического анализа языка прежних версий службы и сканера](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 Описывает анализатор и средство чтения, необходимые для реализации любых функций языковой службы, использующей управляемые границы пакета.  
  
 [Реализация службы языка](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 Описывает, что необходимо для реализующего службу языка с помощью MPF.  
  
 [Регистрация службы языка](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 Описаны шаги, которые необходимы, чтобы зарегистрировать службу языка с MPF\-основанная [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Использование технологии IntelliSense](../../ide/using-intellisense.md)  
 Объясняет, как IntelliSense выполняет справочника по языку легко получить доступ.  
  
 [Реализация службы языка прежних версий](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Предоставляет сведения о том, как использовать управляемые границы пакетов \(MPF\) для ссылки полн\-отличаемую службу языка в управляемом коде.
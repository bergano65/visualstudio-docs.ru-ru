---
title: "Общие сведения о службе устаревших языка | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "языковые службы [платформа управляемых пакетов] о языковые службы"
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# Общие сведения о службе устаревших языка
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Служба языка предоставляет поддержку редактора, которая позволяет реализовать уверенное [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] функции.  Управляемые классы службы языка .NET Framework пакета \(MPF\) обеспечивает полную поддержку для функций част\-используемых и частично поддержку других функций.  
  
## Полностью поддерживаемые функции в MPF  
 Классы службы языка MPF поддерживают следующие функции:  
  
-   Выбор синтаксиса  
  
-   Структуризация  
  
-   Блоки кода комментария  
  
-   Проверка парности фигурных скобок  
  
-   Фрагменты кода  
  
-   Настраиваемые свойства документа  
  
-   Сведения о параметрах IntelliSense  
  
-   Данные IntelliSense быстрые  
  
-   Завершение членов IntelliSense  
  
-   Выполнение машинного слов IntelliSense  
  
## Частично поддерживаемые функции в MPF  
 MPF предоставляет только частично поддержку следующих функций.  Это означает, что необходимо реализовать методы, вызываемые MPF.  
  
-   Переформатирование код.  Необходимо указать код, реализующий переформатирование.  
  
-   Проверка точки останова путем указания допустимых диапазонов кода.  Необходимо указать код, который определяет диапазоны кода.  
  
-   Поддержка отладчика **Видимые** чтобы открыть окно переменные.  Необходимо указать код, который определяет, какие отображаться в окне.  
  
-   Обслуживание **Панель переходов** для быстрого перехода между типами и элементами.  Реализации и возвращает вспомогательный класс, который заполняет списки в **Панель переходов** поля со списком.  
  
## Реализация  
 Необходимо выполнить несколько шагов для реализации службы языка и самой функции языковой службы, которую требуется поддержка для выбранного языка.  Эти шаги рассматриваются в следующих разделах:  
  
-   [Реализация службы языка](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
  
-   [Регистрация службы языка](../../extensibility/internals/registering-a-legacy-language-service1.md)  
  
-   [Синтаксис выделения цветом в языковую службу для прежних версий](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
  
-   [Проверка парности фигурных скобок в языковую службу для прежних версий](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
  
-   [Структуризация в языковую службу для прежних версий](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
  
-   [Комментирование кода в языковую службу для прежних версий](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
  
-   [Форматирование кода в языковую службу для прежних версий](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
  
-   [Пользовательские свойства документа в языковую службу для прежних версий](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
  
-   [Поддержка фрагментов кода в языковую службу для прежних версий](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
  
-   [Поддержка панели навигации в языковую службу для прежних версий](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
  
-   [Завершение слов в языковую службу для прежних версий](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
  
-   [Завершение члена в языковую службу для прежних версий](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
  
-   [Сведения о параметрах в языковую службу для прежних версий](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
  
-   [Краткие сведения в языковую службу для прежних версий](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
  
-   [Поддержка окно видимых переменных в языковую службу для прежних версий](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
  
-   [Проверка точек останова в языковую службу для прежних версий](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
  
## См. также  
 [Реализация службы языка прежних версий](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Расширяемость устаревших языковой службы](../../extensibility/internals/legacy-language-service-extensibility.md)
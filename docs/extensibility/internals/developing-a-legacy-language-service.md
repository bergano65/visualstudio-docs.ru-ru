---
title: "Разработка языковую службу для прежних версий | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.vsip.LangServWiz.langtoks"
  - "vs.vsip.LangServWiz.welcome"
  - "vs.vsip.LangServWiz.langSpec"
  - "vs.vsip.LangServWiz.langInfo"
  - "vs.vsip.LangServWiz.langServOpts"
helpviewer_keywords: 
  - "языковые службы разработки"
ms.assetid: 6151ba88-c1c3-41de-a1cc-668f494d48d1
caps.latest.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 28
---
# Разработка службы языка
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Данном разделе содержатся ссылки на разделы, которые помогут создать устаревших языковой службы.  
  
 Устаревший языковые службы реализуются как частью VSPackage, но это использование расширений MEF новый способ реализации возможностей службы языка. Чтобы больше узнать о новый способ реализации службы языка, в разделе [Редактор и расширения службы языка](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API как можно быстрее. Это улучшает производительность службы языка и позволяют воспользоваться преимуществами новых функций редактора.  
  
## В этом подразделе  
 [Модель службы языка прежних версий](../../extensibility/internals/model-of-a-legacy-language-service.md)  
 Предоставляет модель службы минимальный язык для [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] базового редактора. Эту модель можно использовать как руководство для создания своей собственной службы языка.  
  
 [Интерфейсы службы языка прежних версий](../../extensibility/internals/legacy-language-service-interfaces.md)  
 Описание объектов, необходимых для реализации службы языка и список дополнительных объектов, которые можно использовать для предоставления подсветку синтаксиса, метод данных и другие возможности.  
  
 [Перехват команд службы языка прежних версий](../../extensibility/internals/intercepting-legacy-language-service-commands.md)  
 Описывает, как вставить фильтр команды в вашей службе языка для перехвата команд, которые текстовое представление, в противном случае будет обрабатывать.  
  
 [Регистрация службы языка для прежних версий](../../extensibility/internals/registering-a-legacy-language-service2.md)  
 Содержит сведения о том, как зарегистрировать службу языка с помощью [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Поддержка службы языка для отладки](../../extensibility/internals/language-service-support-for-debugging.md)  
 Описывает, как служба языка может предоставлять функции для поддержки отладчика.  
  
 [Контрольный список: Создание языковую службу для прежних версий](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)  
 Содержит пошаговые инструкции для создания и интеграции службы языка для базового редактора.  
  
## Связанные подразделы  
 [Синтаксиса в языковую службу для прежних версий](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Описывает, как реализовать выделение синтаксиса в службе языка.  
  
 [Завершение операторов в языковую службу для прежних версий](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)  
 Описывает процесс, в котором языковую службу помогает пользователям завершить ключевое слово языка или элемент, они начали ввод завершение операторов.  
  
 [Сведения о параметрах в языковую службу для прежних версий](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)  
 Описание предоставления метода советы для перегруженных функций и методов.  
  
 [Практическое руководство: обеспечивает поддержку скрытого текста в языковую службу для прежних версий](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)  
 Описание назначения области скрытый текст и инструкции о том, как реализовать области скрытый текст.  
  
 [Практическое руководство: обеспечивают расширенную поддержку создания структуры в языковую службу для прежних версий](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)  
 Описание двух параметров, расширения структурирования поддержки для вашего языка только поддерживает *Свернуть в определения* команды.
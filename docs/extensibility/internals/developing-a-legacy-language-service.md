---
title: Разработке службы языка для прежних версий | Документы Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- vs.vsip.LangServWiz.langtoks
- vs.vsip.LangServWiz.welcome
- vs.vsip.LangServWiz.langSpec
- vs.vsip.LangServWiz.langInfo
- vs.vsip.LangServWiz.langServOpts
helpviewer_keywords:
- language services, developing
ms.assetid: 6151ba88-c1c3-41de-a1cc-668f494d48d1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6cf384a22429c6314bf5e2fcbb66db7974d42c87
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/16/2018
ms.locfileid: "31129856"
---
# <a name="developing-a-legacy-language-service"></a>Разработке службы языка для прежних версий
Данном разделе содержатся ссылки на разделы, помогающие создать устаревших языковой службы.  
  
 Прежних версий языка службы реализованы как часть пакета VSPackage, но новой реализации возможностей службы языка можно выполнить с помощью расширений MEF. Чтобы больше узнать о новых способ реализации языковую службу, в разделе [редактора и расширения службы языка](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API, как можно быстрее. Это повысит быстродействие языковой службы и позволяют воспользоваться преимуществами новых функций редактора.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Модель языковой службы прежних версий](../../extensibility/internals/model-of-a-legacy-language-service.md)  
 Предоставляет модель минимальной языковую службу для [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] базового редактора. Эту модель можно использовать в качестве руководства по созданию службы языка.  
  
 [Интерфейсы языковой службы прежних версий](../../extensibility/internals/legacy-language-service-interfaces.md)  
 Описание объектов, необходимых для реализации языковой службы и список дополнительных объектов, которые можно использовать для предоставления подсветку синтаксиса, метод данных и другие возможности.  
  
 [Перехват команд языковой службы прежних версий](../../extensibility/internals/intercepting-legacy-language-service-commands.md)  
 Описывает, как вставить фильтр команды в службе языка для перехвата команды, представления текста, в противном случае будет обрабатываться.  
  
 [Регистрация службы языка для прежних версий](../../extensibility/internals/registering-a-legacy-language-service2.md)  
 Предоставляет сведения о том, как зарегистрировать службу языка с помощью [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Поддержка языковой службы для отладки](../../extensibility/internals/language-service-support-for-debugging.md)  
 Описывает, как языковая служба может предоставлять функции для поддержки отладчика.  
  
 [Контрольный список. Создание языковой службы прежних версий](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)  
 Содержит пошаговые инструкции по созданию и интеграции службы языка для базового редактора.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Цветовая маркировка синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 Описывает, как реализовать подсветку синтаксиса в службе языка.  
  
 [Завершение операторов в языковой службе прежних версий](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)  
 Описывает завершение операторов, процесс, который помогает пользователям завершить ключевое слово языка или элемент, начатую введя языковой службы.  
  
 [Сведения о параметрах в языковую службу прежних версий](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)  
 Описывает, как предоставить метод советы для перегруженных функций и методов.  
  
 [Практическое руководство. Поддержка скрытого текста в языковой службе прежних версий](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)  
 Описание назначения области скрытый текст и инструкции о том, как реализовать области скрытый текст.  
  
 [Практическое руководство. Расширенная поддержка структурирования в языковой службе прежних версий](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)  
 Описание двух параметров, расширения поддержки структурирования язык только поддерживает *свернуть в определения* команды.
---
title: Разработка языковой службы прежних | Документация Майкрософт
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
ms.openlocfilehash: 6d92c07742dcc4433aa96071d655f58d938a1f80
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/03/2018
ms.locfileid: "39497834"
---
# <a name="develop-a-legacy-language-service"></a>Разработка языковой службы прежних версий
Этот раздел содержит ссылки на разделы, которые помогут вам создать языковой службы прежних версий.  
  
 Устаревший языковой службы реализуются как часть пакета VSPackage, но новый способ реализовать функции языковой службы является использование расширений MEF. Чтобы подробнее узнать о новых способах реализации языковой службы, см. в разделе [редактора и языковой службы расширения](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Мы рекомендуем начать использовать новый редактор API как можно скорее. Это улучшит производительность службы языка и позволяют воспользоваться преимуществами новых функций редактора.  
  
## <a name="in-this-section"></a>Содержание раздела  
 [Модель языковой службы прежних версий](../../extensibility/internals/model-of-a-legacy-language-service.md)  
 Предоставляет модель службы минимальный язык для [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] базовым редактором. Эту модель можно использовать в качестве руководства по созданию собственных языковой службы.  
  
 [Интерфейсы служб устаревшего языка](../../extensibility/internals/legacy-language-service-interfaces.md)  
 Описание объектов, необходимых для реализации языковой службы и список дополнительных объектов, которые можно использовать для предоставления возможностей выделения синтаксических конструкций, метод данных и другие функции.  
  
 [Перехват команд устаревший языковой службы](../../extensibility/internals/intercepting-legacy-language-service-commands.md)  
 Описывает, как вставить фильтр команд в службе языка на команды отсекаемый отрезок, представление текста, в противном случае будет обрабатывать.  
  
 [Регистрация языковой службы прежних версий](../../extensibility/internals/registering-a-legacy-language-service2.md)  
 Предоставляет сведения о том, как зарегистрировать службу языка с помощью [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Поддержка языковой службы для отладки](../../extensibility/internals/language-service-support-for-debugging.md)  
 Описывает, как служба языка может предоставлять функциональные возможности для поддержки отладчика.  
  
 [Контрольный список: Создание языковой службы прежних версий](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)  
 Содержит пошаговые инструкции для создания и интеграции службы языка для базового редактора.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Цветовая маркировка синтаксиса в языковой службы прежних версий](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)  
 В этой статье описывается использование подсветки синтаксиса в языковой службы.  
  
 [Завершение операторов в языковой службы прежних версий](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)  
 Описание завершение операторов, процесс, по которому служба языка помогает пользователям, которые Готово ключевое слово языка или элемент, который они начали вводить.  
  
 [Сведения о параметрах в языковой службы прежних версий](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)  
 Описание предоставления подсказок метода для перегруженных функций и методов.  
  
 [Практическое: укажите скрытого текста поддержки в языковой службы прежних версий](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)  
 Описание назначения области скрытого текста и инструкции о том, как реализовать области скрытого текста.  
  
 [Практическое: Расширенная поддержка структурирования в языковой службы прежних версий](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)  
 Описание двух параметров, расширения структуры поддержки для вашего языка, чем поддержка *свернуть в определения* команды.
---
title: Разработка языковой службы «Наследие» (ru) Документы Майкрософт
ms.date: 11/04/2016
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
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0c7f930d5087b6a822156fd44024def0d5b42b49
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708673"
---
# <a name="develop-a-legacy-language-service"></a>Разработка устаревшего языкового сервиса
В этом разделе ссылки на темы, которые помогут вам создать устаревшую языковую службу.

 Устаревшие языковые службы реализуются как часть VSPackage, но новый способ реализации функций языкового сервиса заключается в использовании расширений MEF. Чтобы узнать больше о новом способе реализации языковой [службы, см.](../../extensibility/editor-and-language-service-extensions.md)

> [!NOTE]
> Мы рекомендуем вам начать использовать новый API редактора как можно скорее. Это повысит производительность вашего языкового сервиса и позволит вам воспользоваться новыми функциями редактора.

## <a name="in-this-section"></a>В этом разделе
- [Модель устаревшего языкового сервиса](../../extensibility/internals/model-of-a-legacy-language-service.md)

 Предоставляет модель минимального языкового [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] сервиса для основного редактора. Эту модель можно использовать в качестве руководства для создания собственного языкового сервиса.

- [Устаревшие интерфейсы языковых служб](../../extensibility/internals/legacy-language-service-interfaces.md)

 Обсуждает объекты, необходимые для реализации языковой службы, и предоставляет список дополнительных объектов, которые можно использовать для обеспечения выделения синтаксиса, данных метода и других функций.

- [Перехват устаревших команд языковой службы](../../extensibility/internals/intercepting-legacy-language-service-commands.md)

 Описывает, как вставить командный фильтр в языковую службу для перехвата команд, которые в противном случае было бы обработано текстовым представлением.

- [Регистрация устаревшей языковой службы](../../extensibility/internals/registering-a-legacy-language-service2.md)

 Предоставляет информацию о том, как [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]зарегистрировать свой языковой сервис с помощью .

- [Служба языкового обслуживания для отладки](../../extensibility/internals/language-service-support-for-debugging.md)

 Описывает, как языковая служба может предоставить функции для поддержки отладчика.

- [Контрольный список: Создание устаревшей языковой службы](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)

 Предоставляет пошаговые инструкции по созданию и интеграции языковой службы для основного редактора.

## <a name="related-sections"></a>См. также
- [Раскраска Syntax в устаревшей языковой службе](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)

 Обсуждает, как реализовать выделение синтаксиса в языковой службе.

- [Завершение выполнения заявления в устаревшей языковой службе](../../extensibility/internals/statement-completion-in-a-legacy-language-service.md)

 Обсуждается завершение выполнения оператора, процесс, с помощью которого языковая служба помогает пользователям закончить ключевое слово или элемент языка, который они начали печатать.

- [Информация о параметрах в устаревшей языковой службе](../../extensibility/internals/parameter-info-in-a-legacy-language-service1.md)

 Описывает, как предоставить метод советы для перегруженных функций и методов.

- [Как: Предоставить скрытую поддержку текста в устаревшей языковой службе](../../extensibility/internals/how-to-provide-hidden-text-support-in-a-legacy-language-service.md)

 Объясняет назначение скрытого региона текста и дает инструкции о том, как реализовать область скрытого текста.

- [Как: Обеспечить расширенную поддержку с изложением в устаревшей языковой службе](../../extensibility/internals/how-to-provide-expanded-outlining-support-in-a-legacy-language-service.md)

 Объясняет два варианта, которые расширяют поддержку вашего языка, помимо поддержки команды *«Обюги» команде «Определения».*

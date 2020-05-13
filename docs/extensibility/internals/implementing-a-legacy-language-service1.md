---
title: Внедрение Службы языка наследия1 (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c3805e49ffa83f7dea2ee58ef36e1bc8e48b1eaa
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707700"
---
# <a name="implementing-a-legacy-language-service"></a>Реализация языковой службы прежних версий
Для реализации устаревшей языковой службы, поддерживающей широкий спектр функций, таких как выделение синтаксиса, соответствие скобки и завершение IntelliSense, можно использовать классы в рамках управляемого пакета (MPF).

 Устаревшие языковые службы реализуются как часть VSPackage, но новый способ реализации функций языкового сервиса заключается в использовании расширений MEF. Чтобы узнать больше о новом способе реализации языковой [службы,](../../extensibility/editor-and-language-service-extensions.md)см.

> [!NOTE]
> Мы рекомендуем вам начать использовать новый API редактора как можно скорее. Это повысит производительность вашего языкового сервиса и позволит вам воспользоваться новыми функциями редактора.

## <a name="in-this-section"></a>В этом разделе
- [Обзор языковой службы прежних версий](../../extensibility/internals/legacy-language-service-overview.md)

 Обзор функций языковой службы, которые поддерживаются в MPF.

- [Реализация языковой службы прежних версий](../../extensibility/internals/implementing-a-legacy-language-service2.md)

 Описывает, что необходимо для реализации языковой службы с помощью MPF.

- [Регистрация языковой службы прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md)

 Описывает шаги, которые необходимы для регистрации языковой [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]службы на основе MPF с помощью.

- [Средство синтаксического анализа и сканер языковой службы прежних версий](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

 Описывает два парзера, которые необходимы для реализации всех функций языковой службы с помощью MPF.

- [Пошаговое руководство. Создание языковой службы прежних версий](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)

 Предоставляет основные шаги, необходимые для реализации языковой службы MPF в VSPackage.

- [Пошаговое руководство. Получение списка фрагментов кода (реализация прежних версий)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

 Демонстрирует методы извлечения списка установленных фрагментов кода.

- [Функции языковой службы прежних версий](../../extensibility/internals/legacy-language-service-features1.md)

 Предоставляет ссылки на темы, в которые подробно излагается, что необходимо сделать для реализации всех функций языковой службы с помощью MPF.

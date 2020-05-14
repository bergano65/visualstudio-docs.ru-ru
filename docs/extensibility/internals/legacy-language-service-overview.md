---
title: Обзор Устаревшей языковой службы (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], about language services
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aed653ec200063e72434fc758c7920e6caabafe1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707359"
---
# <a name="legacy-language-service-overview"></a>Обзор языковой службы прежних версий
Языковая служба обеспечивает поддержку редактора, которая позволяет реализовать определенные [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] функции. Классы языковых услуг Managed Package Framework (MPF) обеспечивают полную поддержку часто используемых функций и частичную поддержку других функций.

## <a name="fully-supported-features-in-the-mpf"></a>Полностью поддерживаемые функции в MPF
 Классы языкового сервиса MPF поддерживают следующие функции:

- Выделение синтаксиса

- Структуризация

- Комментируя блоки кода

- Соответствие скобок

- Фрагменты кода

- Свойства пользовательских документов

- Информация о параметрах IntelliSense

- IntelliSense Быстрая информация

- Завершение работы участника IntelliSense

- Завершение слова IntelliSense

## <a name="partially-supported-features-in-the-mpf"></a>Частично поддерживаемые функции в MPF
 MPF обеспечивает лишь частичную поддержку следующих функций. Это означает, что необходимо реализовать методы, которые называются MPF.

- Переформатирование кода. Вы поставляете код, который реализует переформатирование.

- Проверка точек разрыва путем определения допустимых диапазонов кода. Вы поставляете код, который определяет диапазоны кода.

- Поддержка окна отладчика **Autos** для отображения переменных. Вы предоставите код, который определяет, что показывать в окне.

- Поддержка **панели навигации** для быстрой навигации между типами и участниками. Вы реализуете и возвращаете класс помощника, который заполняет списки в комбо-коробках **панели навигации.**

## <a name="implementation"></a>Реализация
 Необходимо выполнить несколько шагов для реализации самой языковой службы и функций языковой службы, которые вы хотите поддерживать для вашего языка. Эти шаги обсуждаются в следующих темах:

- [Реализация языковой службы прежних версий](../../extensibility/internals/implementing-a-legacy-language-service2.md)

- [Регистрация языковой службы прежних версий](../../extensibility/internals/registering-a-legacy-language-service1.md)

- [Цветовая маркировка синтаксиса в языковой службе прежних версий](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)

- [Парные фигурные скобки в языковой службе прежних версий](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)

- [Структурирование в языковой службе прежних версий](../../extensibility/internals/outlining-in-a-legacy-language-service.md)

- [Комментирование кода синтаксиса в языковой службе прежних версий](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)

- [Переформатирование кода в языковой службе прежних версий](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)

- [Настраиваемые свойства документа в языковой службе прежних версий](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)

- [Поддержка фрагментов кода в языковой службе прежних версий](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)

- [Поддержка панели навигации в языковой службе прежних версий](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)

- [Завершение машинных слов в языковой службе прежних версий](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)

- [Завершение участников в языковой службе прежних версий](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)

- [Сведения о параметрах в языковой службе прежних версий](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)

- [Краткие сведения в языковой службе прежних версий](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)

- [Поддержка окна видимых переменных в языковой службе прежних версий](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)

- [Проверка точек останова в языковой службе прежних версий](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)

## <a name="see-also"></a>См. также
- [Реализация языковой службы прежних версий](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Расширяемость языковой службы прежних версий](../../extensibility/internals/legacy-language-service-extensibility.md)

---
title: Обзор языковой службы прежних версий | Документация Майкрософт
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80707359"
---
# <a name="legacy-language-service-overview"></a>Обзор языковой службы прежних версий
Языковая служба предоставляет поддержку редактора, которая позволяет реализовать определенные [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] функции. Классы языковой службы для управляемых пакетов Framework (MPF) обеспечивают полную поддержку часто используемых функций и частичную поддержку других функций.

## <a name="fully-supported-features-in-the-mpf"></a>Полностью поддерживаемые функции в MPF
 Классы языковой службы MPF поддерживают следующие функции:

- Подсветка синтаксиса

- Структуризация

- Комментирование блоков кода

- Соответствие скобок

- Фрагменты кода

- Настраиваемые свойства документа

- Сведения о параметрах IntelliSense

- Краткие сведения о IntelliSense

- Завершение элементов IntelliSense

- Завершение слов IntelliSense

## <a name="partially-supported-features-in-the-mpf"></a>Частично поддерживаемые функции в MPF
 MPF предоставляет только частичную поддержку для следующих функций. Это означает, что необходимо реализовать методы, вызываемые MPF.

- Переформатирование кода. Вы предоставляете код, который реализует переформатирование.

- Проверка точек останова путем определения допустимых диапазонов кода. Укажите код, определяющий диапазоны кода.

- Поддержка окна " **видимые** " отладчика для отображения переменных. Вы предоставляете код, который определяет, что следует отображать в окне.

- Поддержка **панели навигации** для быстрой навигации между типами и членами. Вы реализуете и возвращаете вспомогательный класс, который заполняет списки в полях со списком **панели навигации** .

## <a name="implementation"></a>Реализация
 Для реализации языковой службы и функций языковой службы, которые требуется поддерживать для вашего языка, необходимо выполнить несколько действий. Эти действия описаны в следующих разделах:

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

## <a name="see-also"></a>См. также раздел
- [Реализация языковой службы прежних версий](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Расширяемость языковой службы прежних версий](../../extensibility/internals/legacy-language-service-extensibility.md)

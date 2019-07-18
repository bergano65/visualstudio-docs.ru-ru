---
title: Управление пакетами VSPackage | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b622901ce90187ff8230a8e23a11110e0795b0b5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66340501"
---
# <a name="manage-vspackages"></a>Управление пакетами VSPackage
В большинстве случаев не нужно беспокоиться об управлении пакеты VSPackage, так как шаблоны проектов и элементов, зарегистрировать и автоматически загрузить пакет. Однако в некоторых случаях может потребоваться узнать чуть подробнее для пакета управления.

## <a name="use-the-experimental-instance"></a>Использовать экспериментальный экземпляр
 Чтобы узнать больше о экспериментальный экземпляр, см. в разделе [экспериментальный экземпляр](../extensibility/the-experimental-instance.md).

## <a name="register-and-unregister-vspackages"></a>Регистрация и Отмена регистрации пакетов VSPackage
 Чтобы узнать о регистрации и отмены регистрации пакетов VSPackage и других типах расширения, см. в разделе [регистрации и отмены регистрации пакетов VSPackage](../extensibility/registering-and-unregistering-vspackages.md).

## <a name="load-a-vspackage"></a>Загрузка VSPackage
 Пакеты VSPackage может быть присвоено автозагрузки, когда определенный CMDUICONTEXT GUID включен. Дополнительные сведения см. в разделе [пакетов VSPackage нагрузки](../extensibility/loading-vspackages.md).

## <a name="use-asyncpackage-to-load-vspackages-in-the-background"></a>Использование AsyncPackage для загрузки пакетов VSPackage в фоновом режиме
 `AsyncPackage` Класс обеспечивает загрузку пакета в фоновом потоке для повышения скорости отклика пользовательского интерфейса в Visual Studio. Дополнительные сведения см. в разделе [Практическое руководство. Использование AsyncPackage для загрузки пакетов VSPackage в фоновом режиме](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md).

## <a name="rule-based-ui-context-for-extensions"></a>Контекст пользовательского интерфейса на основе правил для расширений
 Контексты пользовательского интерфейса на основе правил позволяет разработчикам расширений определить точные условия, при которых активируется контекст пользовательского интерфейса и загружаются связанные пакеты VSPackage. Дополнительные сведения см. в разделе [Практическое руководство. Использовать контекст пользовательского интерфейса на основе правил для расширений Visual Studio](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md).

## <a name="diagnose-extension-performance"></a>Диагностика производительности расширения
Расширения могут повлиять на производительность загрузки для загрузки и решение. Узнайте, как вычисляется влияние расширения Visual Studio и как их можно проанализировать локально для тестирования, если расширение может отображаться как производительности, влияющие на расширение. Дополнительные сведения см. в разделе [Практическое руководство. Диагностика производительности расширения](how-to-diagnose-extension-performance.md).

## <a name="troubleshoot-vspackages"></a>Устранение неполадок пакетов VSPackage
 Найти методы устранения неполадок пакетов VSPackage, не загружаются или при возникновении ошибки: [Устранение неполадок пакетов VSPackage](../extensibility/troubleshooting-vspackages.md)

## <a name="see-also"></a>См. также
- [Пакеты VSPackage](../extensibility/internals/vspackages.md)
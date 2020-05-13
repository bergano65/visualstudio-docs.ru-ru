---
title: Управление VSPackages (ru) Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60745d07679ae53b85d169473ed37ab314b67624
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702655"
---
# <a name="manage-vspackages"></a>Управление пакетами VSPackage
В большинстве случаев вам не нужно беспокоиться об управлении VSPackages, так как шаблоны проекта и элемента регистрируются и загружают пакет автоматически. Тем не менее, в некоторых случаях вам может понадобиться узнать немного больше для того, чтобы управлять своим пакетом.

## <a name="use-the-experimental-instance"></a>Использование экспериментального экземпляра
 Чтобы узнать больше об экспериментальном экземпляре, [см.](../extensibility/the-experimental-instance.md)

## <a name="register-and-unregister-vspackages"></a>Регистрация и распаковка VSPackages
 Чтобы узнать, как зарегистрировать и отменить VSPackages и другие виды расширения, [см.](../extensibility/registering-and-unregistering-vspackages.md)

## <a name="load-a-vspackage"></a>Загрузить VSPackage
 VSPackages можно настроить для автоматической загрузки при включении конкретного GUID CMDUICONTEXT. Для получения дополнительной [информации см.](../extensibility/loading-vspackages.md)

## <a name="use-asyncpackage-to-load-vspackages-in-the-background"></a>Используйте AsyncPackage для загрузки VSPackages в фоновом режиме
 Класс `AsyncPackage` позволяет загрузить пакет на фоновый поток для лучшей отзывчивости uI в Visual Studio. Для получения дополнительной [информации см. Как: Используйте AsyncPackage для загрузки VSPackages в фоновом режиме.](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md)

## <a name="rule-based-ui-context-for-extensions"></a>Контекст uI на основе правил для расширений
 Контексты uI, основанные на правилах, позволяют авторам расширения определить точные условия, при которых активируется контекст uI и загружается связанные с ними VSPackages. Для получения дополнительной информации [см. Как: Используйте контекст uI на основе правил для расширений Visual Studio.](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md)

## <a name="diagnose-extension-performance"></a>Диагностика производительности расширения
Расширения могут повлиять на производительность загрузки стартапа и решения. Узнайте, как рассчитывается влияние расширения Visual Studio и как его можно анализировать локально, чтобы проверить, может ли расширение отображаться как расширение, влияющие на производительность. Для получения дополнительной информации [см.](how-to-diagnose-extension-performance.md)

## <a name="troubleshoot-vspackages"></a>Устранение неприятностей VSPackages
 Узнайте о методах устранения неполадок VSPackages, которые не загружаются или испытывают ошибки: [Troubleshoot VSPackages](../extensibility/troubleshooting-vspackages.md)

## <a name="see-also"></a>См. также
- [Пакеты VSPackage](../extensibility/internals/vspackages.md)

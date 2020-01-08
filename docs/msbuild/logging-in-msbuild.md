---
title: Ведение журнала в MSBuild | Документы Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, logging
ms.assetid: 9aea2e76-8f60-4234-913d-598e7bbad808
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 24a769f6d0b9aa847899c02c951921dc77bac21a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592195"
---
# <a name="logging-in-msbuild"></a>Ведение журнала в MSBuild
Ведение журнала позволяет следить за ходом выполнения сборки. При ведении журнала в файл записываются события сборки, сообщения, предупреждения и ошибки.

## <a name="in-this-section"></a>Содержание раздела
- [Получение журналов сборки](../msbuild/obtaining-build-logs-with-msbuild.md)

 Описываются различные аспекты ведения журнала в [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].

- [Средства ведения журнала сборки](../msbuild/build-loggers.md)

 Описываются действия по созданию однопроцессорного средства ведения журнала.

- [Ведение журнала в многопроцессорной среде](../msbuild/logging-in-a-multi-processor-environment.md)

 Описываются способы ведения журнала в многопроцессорной среде и демонстрируются две модели ведения журналов.

- [Запись средств ведения журнала с поддержкой многопроцессорности](../msbuild/writing-multi-processor-aware-loggers.md)

 Описываются способы создания средств ведения журнала с поддержкой нескольких процессоров и способы использования ConfigurableForwardingLogger.

- [Создание средства ведения журнала с перенаправлением](../msbuild/creating-forwarding-loggers.md)

 Описываются способы создания пользовательских средств ведения журнала переадресации.

## <a name="see-also"></a>См. также
- [Параллельная сборка нескольких проектов](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md). Описывается быстрый способ сборки нескольких проектов с использованием параллельного запуска.

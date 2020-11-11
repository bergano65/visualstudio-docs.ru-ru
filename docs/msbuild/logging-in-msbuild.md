---
title: Ведение журнала в MSBuild | Документы Майкрософт
description: Узнайте, как ведение журнала MSBuild позволяет отслеживать ход выполнения сборки благодаря записи событий сборки, сообщений, предупреждений и ошибок в файл журнала.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 9de830003571f1f648cf06be634d9a773b95269f
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/28/2020
ms.locfileid: "92904329"
---
# <a name="logging-in-msbuild"></a>Ведение журнала в MSBuild

Ведение журнала позволяет следить за ходом выполнения сборки. При ведении журнала в файл записываются события сборки, сообщения, предупреждения и ошибки.

## <a name="in-this-section"></a>В этом разделе

- [Получение журналов сборки](../msbuild/obtaining-build-logs-with-msbuild.md)

 Описываются различные аспекты ведения журнала в MSBuild.

- [Средства ведения журнала сборки](../msbuild/build-loggers.md)

 Описываются действия по созданию однопроцессорного средства ведения журнала.

- [Ведение журнала в многопроцессорной среде](../msbuild/logging-in-a-multi-processor-environment.md)

 Описываются способы ведения журнала в многопроцессорной среде и демонстрируются две модели ведения журналов.

- [Написание средств ведения журнала с поддержкой многопроцессорности](../msbuild/writing-multi-processor-aware-loggers.md)

 Описываются способы создания средств ведения журнала с поддержкой нескольких процессоров и способы использования ConfigurableForwardingLogger.

- [Создание средства ведения журнала с перенаправлением](../msbuild/creating-forwarding-loggers.md)

 Описываются способы создания пользовательских средств ведения журнала переадресации.

## <a name="see-also"></a>См. также раздел

- [Параллельная сборка нескольких проектов](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md). Описывается быстрый способ сборки нескольких проектов с использованием параллельного запуска.

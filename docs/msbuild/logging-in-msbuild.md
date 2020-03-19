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
ms.openlocfilehash: a66164426b760798571fc35e5288158a8dae9943
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633555"
---
# <a name="logging-in-msbuild"></a>Ведение журнала в MSBuild

Ведение журнала позволяет следить за ходом выполнения сборки. При ведении журнала в файл записываются события сборки, сообщения, предупреждения и ошибки.

## <a name="in-this-section"></a>Содержание раздела

- [Получение журналов сборки](../msbuild/obtaining-build-logs-with-msbuild.md)

 Описываются различные аспекты ведения журнала в MSBuild.

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

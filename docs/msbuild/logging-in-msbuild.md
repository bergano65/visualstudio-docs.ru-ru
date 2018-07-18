---
title: Ведение журнала в MSBuild | Документы Майкрософт
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, logging
ms.assetid: 9aea2e76-8f60-4234-913d-598e7bbad808
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 80a73f2433f942c35413f77143203c06cd9447a5
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/19/2018
ms.locfileid: "31567997"
---
# <a name="logging-in-msbuild"></a>Ведение журнала в MSBuild
Ведение журнала позволяет следить за ходом выполнения сборки. При ведении журнала в файл записываются события сборки, сообщения, предупреждения и ошибки.  
  
## <a name="in-this-section"></a>В этом разделе  
 [Получение журналов сборки](../msbuild/obtaining-build-logs-with-msbuild.md)  
 Описываются различные аспекты ведения журнала в [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)].  
  
 [Средства ведения журнала сборки](../msbuild/build-loggers.md)  
 Описываются действия по созданию однопроцессорного средства ведения журнала.  
  
 [Ведение журнала в многопроцессорной среде](../msbuild/logging-in-a-multi-processor-environment.md)  
 Описываются способы ведения журнала в многопроцессорной среде и демонстрируются две модели ведения журналов.  
  
 [Написание средств ведения журнала с поддержкой многопроцессорности](../msbuild/writing-multi-processor-aware-loggers.md)  
 Описываются способы создания средств ведения журнала с поддержкой нескольких процессоров и способы использования ConfigurableForwardingLogger.  
  
 [Создание средства ведения журнала переадресации](../msbuild/creating-forwarding-loggers.md)  
 Описываются способы создания пользовательских средств ведения журнала переадресации.  
  
## <a name="related-sections"></a>Связанные разделы  
 [Параллельная сборка нескольких проектов](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)  
 Описывается быстрый способ сборки нескольких проектов с использованием параллельного запуска.
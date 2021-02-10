---
title: Эффективное использование памяти при сборке больших проектов | Документы Майкрософт
description: Узнайте, как MSBuild автоматически управляет памятью, например выгружая старые версии и получая кэши, при построении больших проектов.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 99cee9cfbf779bbee97c00fb76f9670e1d609b00
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965906"
---
# <a name="use-memory-efficiently-when-you-build-large-projects"></a>Эффективное использование памяти при построении больших проектов

Большие проекты часто содержат множество подпроектов и других зависимостей, которые могут занимать большой объем системной памяти во время сборки. При уменьшении доступной системной памяти может снижаться и производительность системы. Более старые версии проектов MSBuild оставались в памяти. В версии 3.5 старые версии проектов удаляются, но результаты сборки сохраняются в кэше, чтобы их можно было получить в дальнейшем.

 Версия 4.0 осуществляет подобное управление памятью автоматически, устраняя потребность в использовании для проектов таких свойств, как `UnloadProjectsOnCompletion` и `UseResultsCache`.

### <a name="see-also"></a>См. также раздел

- [Параллельная сборка нескольких проектов](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)

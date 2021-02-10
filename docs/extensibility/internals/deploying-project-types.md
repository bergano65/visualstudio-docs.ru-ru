---
title: Развертывание типов проектов | Документация Майкрософт
description: Узнайте, как развертывать типы проектов с управляемым кодом с помощью нового агрегатора типа проекта и установщик Windows пакета для повторного распространения в пакете SDK для Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e717064318372b31e13d97381ee03d5986a9de2e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965321"
---
# <a name="deploy-project-types"></a>Развертывание типов проектов
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] устанавливает новый агрегатор типа проекта (*ProjectAggregator2.dll*), а также пакет установщик Windows для распространения (*ProjectAggregator2.msi*). Для типов проектов с управляемым кодом необходимо использовать новый агрегатор. ProjectAggregator2 работает с ограничениями в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] агрегаторе проекта, что предотвращает неправильную работу типов проектов управляемого кода. Следующие шаги описывают, как изменить пакет VSPackage для использования новой агрегаторы.

1. Удалите проект Нативехиерарчивраппер из решения.

2. Удалите из программы установки все двоичные файлы Нативехиерарчивраппер.

3. Добавьте *ProjectAggregator2.msi* в программу установки.

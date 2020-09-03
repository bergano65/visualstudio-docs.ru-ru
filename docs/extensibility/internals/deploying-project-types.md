---
title: Развертывание типов проектов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 835e85ade4d309d0b5692aa9b857476cd6b5927a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708792"
---
# <a name="deploy-project-types"></a>Развертывание типов проектов
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] устанавливает новый агрегатор типа проекта (*ProjectAggregator2.dll*), а также пакет установщик Windows для распространения (*ProjectAggregator2.msi*). Для типов проектов с управляемым кодом необходимо использовать новый агрегатор. ProjectAggregator2 работает с ограничениями в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] агрегаторе проекта, что предотвращает неправильную работу типов проектов управляемого кода. Следующие шаги описывают, как изменить пакет VSPackage для использования новой агрегаторы.

1. Удалите проект Нативехиерарчивраппер из решения.

2. Удалите из программы установки все двоичные файлы Нативехиерарчивраппер.

3. Добавьте *ProjectAggregator2.msi* в программу установки.

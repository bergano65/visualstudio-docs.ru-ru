---
title: Развертывание типов проектов | Документация Майкрософт
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac03682fa1158f5da9c694cf1be5282717c07b55
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66312176"
---
# <a name="deploy-project-types"></a>Развертывание типов проектов
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] устанавливает новые средства инвентаризации программного обеспечения типа проекта (*ProjectAggregator2.dll*) и также пакет установщика Windows для распространения (*ProjectAggregator2.msi*). Необходимо использовать новые средства инвентаризации программного обеспечения для типов проектов управляемого кода. ProjectAggregator2 предназначена для обхода ограничения в [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] проект средства инвентаризации программного обеспечения, которое препятствует правильной работе типы проектов управляемого кода. Далее описано изменение VSPackage для использования нового средства инвентаризации программного обеспечения.

1. Удалите NativeHierarchyWrapper проект из решения.

2. Удалите NativeHierarchyWrapper двоичные файлы из пакета установки.

3. Добавить *ProjectAggregator2.msi* на настройки.